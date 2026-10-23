Installing the driver does not always create a **CUPS printer queue**. On Arch, add it like this:

1. Start the print service:

   ```bash
   sudo pacman -S --needed cups
   sudo systemctl enable --now cups.service
   ```

2. Open [http://localhost:631](http://localhost:631), then go to **Administration → Add Printer**.

3. Select the Brother printer under discovered printers. If it is not listed, find its connection address with:

   ```bash
   lpinfo -v
   ```

   Use the reported `usb://...` or network address. For a network printer whose IP address you know, you can try `ipp://PRINTER_IP/ipp/print`.

4. At the driver selection screen, choose **Brother MFC-L3760CDW**. If it is absent, check whether CUPS can see the installed driver:

Choose “Brother MFCL3760CDW CUPS (en)” — the fourth entry. That uses the Brother driver you installed. The fifth entry has the same label, so either of those two should work. Click Add Printer, then print a test page.

   ```bash
   lpinfo -m | grep -i '3760'
   ```

   You can also choose **Provide a PPD File** and select the `.ppd` installed by your driver package. Finish with **Add Printer**, then print a test page from the printer’s CUPS page.

To confirm the queue was added, run `lpstat -t`. If `lpinfo -m` finds nothing, check how `mfcl3760cdwpdrv` was installed and whether the printer is connected by USB or network; that determines the exact driver path and connection address.




