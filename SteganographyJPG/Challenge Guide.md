# Challenge Guide | Difficulty: Medium

## Requirements:

- Reading of file using HEX Editor
- Some knowledge of file markers (JPG image marker + trailer)

This challenge is **`Part 2`** to a series of challenges:

1. MetadataForensic : flag@179369
2. **SteganographyJPG** : flag@singaporezoo
3. OSINTGitHistory : flag@notsohiddenanymore

---

## Steps:

1.  Use a `Hex editor` to view the binary data of `alamak.jpg`.

    I will be using a Hex Editor called [Bless](https://github.com/bwrsandman/Bless).

    ```bash
    $ bless alamak.jpg
    ```

    ![Bless Editor](Guide-Media/2022-05-15%2020-41.png)

2.  Find for JPG image hex markers.

    JPEG files (compressed images) start with an `image marker` which always contains the marker code hex values:

         FF D8 FF

    In our case, we have 2 matches for the marker ode `FF D8 FF`.
    Once at the start of the file and near the middle of the file This signifies that there might be actually two jpg instead of one.

    ![First JPG Marker](Guide-Media/2022-05-15%2020-50.png)
    ![Second JPG Marker](Guide-Media/2022-05-15%2020-44.png)

3.  Confirm this by finding JPG end signature.

    JPEG files have a `trailer` to signify the end of the file since, it does not have the length of file embedded.

        FF D9

    In our case, we indeed have 2 matches for this trailer, one found right before the second `FF D8 FF`.

    ![First JPG Trailer](Guide-Media/2022-05-15%2020-49.png)
    ![Second JPG Trailer](Guide-Media/2022-05-15%2020-49_1.png)

4.  Remove from first image marker to first trailer.

    ![Remove First JPG](Guide-Media/2022-05-15%2021-07.png)

5.  Save the new file.

    The flag is found in the new image.

        flag@singaporezoo

    ![Flag](Guide-Media/2022-05-15%2021-10.png)
