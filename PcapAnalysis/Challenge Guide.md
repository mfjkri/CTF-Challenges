# PcapAnalysis | Difficulty: Medium

## Requirements:

- Anaylzing PCAP file using software like Wireshark
- Identify SMTP packet with attachment data containing base64 string
- Convert Base64 into a file (zip file)
- Identify DNS packet with password key needed to unlock zip file

---

## Steps:

1. Open `tcp_dump.pcap` using any packet analysis software you want. I will be using `Wireshark`.
2. Identify the `packet` that contains the attachment sent via email (SMTP).
   ![Wireshark](Guide-Media/2022-05-11%2017-11.png)

   You may choose to open the packet in a new window.
   ![Packet View](Guide-Media/2022-05-11%2017-18.png)

3. Copy the Base64 string and convert it back into a file.

   ```
   BASE64_STRING = """[UEsDBAoAAAAAAOxq6VIAAAAAAAAAAAAAAAAHABwAbmVidWxhL1VUCQADS93nYCrd52B1eAsAAQToAwAABOoDAABQSwMECgAJAAAA7GrpUvmMGIEiAAAAFgAAABMAHABuZWJ1bGEvY29udGFjdHMudHh0VVQJAANL3edgS93nYHV4CwABBOgDAAAE6gMAAICXO9IVpzqkNdJRu51eykXn9x0nFanSMPfL65HdRmXD4eBQSwcI+YwYgSIAAAAWAAAAUEsDBAoACQAAAHpo6VKUwahkHAAAABAAAAARABwAbmVidWxhL3NlY3JldC50eHRVVAkAA7fY52C32OdgdXgLAAEE6AMAAATqAwAAsYLQLQ2AQL+fwhANfVRnAv552NMMhutLypH6xFBLBwiUwahkHAAAABAAAABQSwECHgMKAAAAAADsaulSAAAAAAAAAAAAAAAABwAYAAAAAAAAABAA7UEAAAAAbmVidWxhL1VUBQADS93nYHV4CwABBOgDAAAE6gMAAFBLAQIeAwoACQAAAOxq6VL5jBiBIgAAABYAAAATABgAAAAAAAEAAACkgUEAAABuZWJ1bGEvY29udGFjdHMudHh0VVQFAANL3edgdXgLAAEE6AMAAATqAwAAUEsBAh4DCgAJAAAAemjpUpTBqGQcAAAAEAAAABEAGAAAAAAAAQAAAKSBwAAAAG5lYnVsYS9zZWNyZXQudHh0VVQFAAO32OdgdXgLAAEE6AMAAATqAwAAUEsFBgAAAAADAAMA/QAAADcBAAAAAA=="""

   ```

   I will be using `Python` to convert the base64 string into a file.

   ```
    import base64

    decoded_bytes = base64.b64decode(BASE64_STRING)

    with open("nebula.zip", "wb") as nebula_zip:
        nebula_zip.write(decoded_bytes)
   ```

   You should now have a zip file called `nebula.zip` that is password protected.

4. Locate the `packet` with the zip file password.
   ![Zip file password](Guide-Media/2022-05-11%2017-34.png)

```
Password is: q1w2e3r4
```

5. Unlock and unzip the file using any zip software you want.

   Flag is found in `secrets.txt`.
