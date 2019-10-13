# PROBLEM SET

#### Whodunit:

https://lab.cs50.io/cs50/labs/2019/x/whodunit/

###### My solution:

```c
// Copies a BMP file

#include <stdio.h>
#include <stdlib.h>

#include "bmp.h"

int main(int argc, char *argv[])
{
    // ensure proper usage
    if (argc != 3)
    {
        printf("Usage: copy infile outfile\n");
        return 1;
    }

    // remember filenames
    char *infile = argv[1];
    char *outfile = argv[2];

    // open input file
    FILE *inptr = fopen(infile, "r");
    if (inptr == NULL)
    {
        printf("Could not open %s.\n", infile);
        return 2;
    }

    // open output file
    FILE *outptr = fopen(outfile, "w");
    if (outptr == NULL)
    {
        fclose(inptr);
        printf("Could not create %s.\n", outfile);
        return 3;
    }

    // read infile's BITMAPFILEHEADER
    BITMAPFILEHEADER bf;
    fread(&bf, sizeof(BITMAPFILEHEADER), 1, inptr);

    // read infile's BITMAPINFOHEADER
    BITMAPINFOHEADER bi;
    fread(&bi, sizeof(BITMAPINFOHEADER), 1, inptr);

    // ensure infile is (likely) a 24-bit uncompressed BMP 4.0
    if (bf.bfType != 0x4d42 || bf.bfOffBits != 54 || bi.biSize != 40 ||
        bi.biBitCount != 24 || bi.biCompression != 0)
    {
        fclose(outptr);
        fclose(inptr);
        printf("Unsupported file format.\n");
        return 4;
    }

    // write outfile's BITMAPFILEHEADER
    fwrite(&bf, sizeof(BITMAPFILEHEADER), 1, outptr);

    // write outfile's BITMAPINFOHEADER
    fwrite(&bi, sizeof(BITMAPINFOHEADER), 1, outptr);

    // determine padding for scanlines
    int padding = (4 - (bi.biWidth * sizeof(RGBTRIPLE)) % 4) % 4;

    // iterate over infile's scanlines
    for (int i = 0, biHeight = abs(bi.biHeight); i < biHeight; i++)
    {
        // iterate over pixels in scanline
        for (int j = 0; j < bi.biWidth; j++)
        {
            // temporary storage
            RGBTRIPLE triple;
            triple.rgbtBlue = 0xff;
            triple.rgbtGreen = 0xff;
            triple.rgbtRed = 0xff;
            
            // read RGB triple from infile
            fread(&triple, sizeof(RGBTRIPLE), 1, inptr);
            
            if (triple.rgbtBlue == triple.rgbtGreen && triple.rgbtGreen == triple.rgbtRed && triple.rgbtRed >= 0)
            {
                triple.rgbtBlue = 0x00;
                triple.rgbtGreen = 0x00;
                triple.rgbtRed = 0x00;
            }
            /*else if (triple.rgbtRed == 0xff)
            {
                triple.rgbtBlue = 0xff;
                triple.rgbtGreen = 0xff;
                triple.rgbtRed = 0xff;
            }*/
            
            //triple.rgbtRed += 10;
                
            // write RGB triple to outfile
            fwrite(&triple, sizeof(RGBTRIPLE), 1, outptr);
        }

        // skip over padding, if any
        fseek(inptr, padding, SEEK_CUR);

        // then add it back (to demonstrate how)
        for (int k = 0; k < padding; k++)
        {
            fputc(0x00, outptr);
        }
    }

    // close infile
    fclose(inptr);

    // close outfile
    fclose(outptr);

    // success
    return 0;
}


```

#### Resize less:

https://docs.cs50.net/2019/x/psets/3/resize/less/resize.html

######Soultion 1 (recopy):

```c
// Copies a BMP file

#include <stdio.h>
#include <stdlib.h>

#include "bmp.h"

int main(int argc, char *argv[])
{
    // ensure proper usage
    if (argc != 4)
    {
        fprintf(stderr, "Usage: copy n infile outfile\n");
        return 1;
    }

    // resize factor
    int n = atoi(argv[1]);

    // remember filenames
    char *infile = argv[2];
    char *outfile = argv[3];

    // open input file
    FILE *inptr = fopen(infile, "r");
    if (inptr == NULL)
    {
        fprintf(stderr, "Could not open %s.\n", infile);
        return 2;
    }

    // open output file
    FILE *outptr = fopen(outfile, "w");
    if (outptr == NULL)
    {
        fclose(inptr);
        fprintf(stderr, "Could not create %s.\n", outfile);
        return 3;
    }

    // read infile's BITMAPFILEHEADER
    BITMAPFILEHEADER bf;
    fread(&bf, sizeof(BITMAPFILEHEADER), 1, inptr);

    // read infile's BITMAPINFOHEADER
    BITMAPINFOHEADER bi;
    fread(&bi, sizeof(BITMAPINFOHEADER), 1, inptr);

    // ensure infile is (likely) a 24-bit uncompressed BMP 4.0
    if (bf.bfType != 0x4d42 || bf.bfOffBits != 54 || bi.biSize != 40 ||
        bi.biBitCount != 24 || bi.biCompression != 0)
    {
        fclose(outptr);
        fclose(inptr);
        fprintf(stderr, "Unsupported file format.\n");
        return 4;
    }

    // determine padding for scanlines of infile
    int inpadding = (4 - (bi.biWidth * sizeof(RGBTRIPLE)) % 4) % 4;

    // determine for padding for scanlines of outfile
    int outpadding = (4 - (bi.biWidth * n * sizeof(RGBTRIPLE)) % 4) % 4;

    // change outfile's BITMAPINFOHEADER
    bi.biWidth *= n;
    bi.biHeight *= n;
    bi.biSizeImage = ((sizeof(RGBTRIPLE) * bi.biWidth) + outpadding) * abs(bi.biHeight) ; //why abs? because height can be negative

    // change outfile's BITMAPFILEHEADER
    bf.bfSize = bi.biSizeImage + sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER);

    // write outfile's BITMAPFILEHEADER
    fwrite(&bf, sizeof(BITMAPFILEHEADER), 1, outptr);

    // write outfile's BITMAPINFOHEADER
    fwrite(&bi, sizeof(BITMAPINFOHEADER), 1, outptr);

    // iterate over infile's scanlines
    for (int i = 0, biHeight = abs(bi.biHeight) / n; i < biHeight; i++) // devide by n because we multiplied by n earlier
    {
        for (int l = 0; l < n; l++)
        {
            // iterate over pixels in scanline
            for (int j = 0; j < bi.biWidth / n; j++) //devide by n because we multiplied by n earlier
            {
                // temporary storage
                RGBTRIPLE triple;

                // read RGB triple from infile
                fread(&triple, sizeof(RGBTRIPLE), 1, inptr);

                // write to outfile n times
                for (int k = 0; k < n; k++)
                {
                    // write RGB triple to outfile
                    fwrite(&triple, sizeof(RGBTRIPLE), 1, outptr);
                }
            }

            // add padding to outfile
            for (int k = 0; k < outpadding; k++)
            {
                fputc(0x00, outptr);
            }

            // send infile cursor back
            if (l != n - 1)
            {
                fseek(inptr, -((bi.biWidth / n) * 3), SEEK_CUR); // fseek goes back in bytes therefore we multiply num. of pixels by bytes in each pixel ie 3
            }
        }

        // skip over padding, if any
        fseek(inptr, inpadding, SEEK_CUR);
    }

    // close infile
    fclose(inptr);

    // close outfile
    fclose(outptr);

    // success
    return 0;
}

```

###### Solution 2 (rewrite):

```c
// Copies a BMP file

#include <stdio.h>
#include <stdlib.h>

#include "bmp.h"

int main(int argc, char *argv[])
{
    // ensure proper usage
    if (argc != 4)
    {
        fprintf(stderr, "Usage: copy n infile outfile\n");
        return 1;
    }

    // resize factor
    int n = atoi(argv[1]);

    // remember filenames
    char *infile = argv[2];
    char *outfile = argv[3];

    // open input file
    FILE *inptr = fopen(infile, "r");
    if (inptr == NULL)
    {
        fprintf(stderr, "Could not open %s.\n", infile);
        return 2;
    }

    // open output file
    FILE *outptr = fopen(outfile, "w");
    if (outptr == NULL)
    {
        fclose(inptr);
        fprintf(stderr, "Could not create %s.\n", outfile);
        return 3;
    }

    // read infile's BITMAPFILEHEADER
    BITMAPFILEHEADER bf;
    fread(&bf, sizeof(BITMAPFILEHEADER), 1, inptr);

    // read infile's BITMAPINFOHEADER
    BITMAPINFOHEADER bi;
    fread(&bi, sizeof(BITMAPINFOHEADER), 1, inptr);

    // ensure infile is (likely) a 24-bit uncompressed BMP 4.0
    if (bf.bfType != 0x4d42 || bf.bfOffBits != 54 || bi.biSize != 40 ||
        bi.biBitCount != 24 || bi.biCompression != 0)
    {
        fclose(outptr);
        fclose(inptr);
        fprintf(stderr, "Unsupported file format.\n");
        return 4;
    }

    // determine padding for scanlines of infile
    int inpadding = (4 - (bi.biWidth * sizeof(RGBTRIPLE)) % 4) % 4;

    //Determine for padding for scanlines of outfile
    int outpadding = (4 - (bi.biWidth * n * sizeof(RGBTRIPLE)) % 4) % 4;

    //change outfile's BITMAPINFOHEADER
    bi.biWidth *= n;
    bi.biHeight *= n;
    bi.biSizeImage = ((sizeof(RGBTRIPLE) * bi.biWidth) + outpadding) * abs(bi.biHeight) ; //why abs? because height can be negative

    // change outfile's BITMAPFILEHEADER
    bf.bfSize = bi.biSizeImage + sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER);

    // write outfile's BITMAPFILEHEADER
    fwrite(&bf, sizeof(BITMAPFILEHEADER), 1, outptr);

    // write outfile's BITMAPINFOHEADER
    fwrite(&bi, sizeof(BITMAPINFOHEADER), 1, outptr);

    // Temporary array of RGBTRIPLE's
    RGBTRIPLE row[sizeof(RGBTRIPLE) * bi.biWidth];

    // iterate over infile's scanlines
    for (int i = 0, biHeight = abs(bi.biHeight) / n; i < biHeight; i++)
    {
        int m = 0;

        // iterate over pixels in scanline
        for (int j = 0; j < bi.biWidth / n; j++)
        {
            // temporary storage
            RGBTRIPLE triple;

            // read RGB triple from infile
            fread(&triple, sizeof(RGBTRIPLE), 1, inptr);

            // write to row n times
            for(int k = 0; k < n; k++)
            {
                // write RGB triple to row
                row[m] = triple;
                m++;
            }
        }
        for(int j = 0; j < n; j++)
        {
            for(int k = 0; k < m; k++)
            {
                fwrite(&row[k], sizeof(RGBTRIPLE), 1, outptr );
            }

            // then add it back (to demonstrate how)
            for (int k = 0; k < outpadding; k++)
            {
                fputc(0x00, outptr);
            }
        }

        // skip over padding, if any
        fseek(inptr, inpadding, SEEK_CUR);
    }

    // close infile
    fclose(inptr);

    // close outfile
    fclose(outptr);

    // success
    return 0;
}

```



#### Recover:

https://docs.cs50.net/2019/x/psets/3/recover/recover.html

###### My solution:

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
    // check it there are two arguments in the command line 
    if (argc != 2)
    {
        fprintf(stderr, "Usage ./recover Image\n");
        return 1;
    }
    
    // open card file 
    FILE *file = fopen(argv[1], "r");
    if (file == NULL)
    {
        fprintf(stderr, "Couldn't open %s", argv[1]);
        return 2;
    }
    
    // buffer
    unsigned char *buffer = malloc(513);
    buffer[512] = 0x00;
    
    // number
    int number = 512;
    
    // bool
    int jpegFound = 0;
    
    // jpeg number
    int jpegNum = 0;
    
    // jpeg name  
    char *jpegName = malloc(8);
    jpegName[7] = 0x00; 
    
    // jpeg file pointer
    FILE *jpegPtr;
    
    // iterate through all the blocks of the card
    while (1)
    {
        // read 512 bytes into a buffer
        number = fread(buffer, 1, 512, file);
        
        // break out of the loop if its the EOF
        if (number != 512)
        {
            break;
        }
        
        // check whether its the start of a new jpeg
        if (buffer[0] == 0xff && buffer[1] == 0xd8 && buffer[2] == 0xff && (buffer[3] & 0xf0) == 0xe0)
        {
            // have we already found a jpeg?
            if (jpegFound == 1)
            {
                // increment jpegNum
                jpegNum++;
                
                // close previous jpeg file
                fclose(jpegPtr);
                
                // store the jpegName in a string
                sprintf(jpegName, "%03i.jpg", jpegNum);
                
                // open a new file with the stored jpeg name
                jpegPtr = fopen(jpegName, "w");
            }
            else
            {
                // we found a jpeg finally
                jpegFound = 1;
                
                // store the jpeg Name in a string
                sprintf(jpegName, "%03i.jpg", jpegNum);
                
                // open a new file with the stored jpeg name
                jpegPtr = fopen(jpegName, "w");
            }
            
            // write buffer to the jpeg
            fwrite(buffer, 1, 512, jpegPtr);
        }
        else
        {
            if (jpegFound == 1)
            {
                // this means that these bytes are part of the previous jpeg
                fwrite(buffer, 1, 512, jpegPtr);
            }
            else
            {
                // this means that these bytes can be discarded
            }
        }
    }
    
    // close any remaining files
    fclose(jpegPtr);
    
    // free the memory we used in malloc
    free(buffer);
    free(jpegName);
    
    // return 0
    return 0;
}
```



