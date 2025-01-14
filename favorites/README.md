# Responsive Dashboard with Hyperlinks

This project is a simple responsive dashboard that displays a list of tiles with hyperlinks. The links and titles are read from a CSV file, and the tiles are dynamically generated using JavaScript.

## Installation

Copy the complete folder in the folder `/var/www/`.
You FTP (Filezilla or WinSCP) in order to do so.
You should have the following folder tree 
/var/www/favorites/
/var/www/favorites/styles.css
/var/www/favorites/script.js
/var/www/favorites/index.html
/var/www/favorites/links.csv

##. **Add your favorites in the `links.csv` file :**

   ```csv
   Title,URL
   Tile 1,https://www.example1.com
   Tile 2,https://www.example2.com
   Tile 3,https://www.example3.com
   Tile 4,https://www.example4.com
   Tile 5,https://www.example5.com
   Tile 6,https://www.example6.com
   Tile 7,https://www.example7.com
   Tile 8,https://www.example8.com
   Tile 9,https://www.example9.com
   Tile 10,https://www.example10.com
   Tile 11,https://www.example11.com
   Tile 12,https://www.example12.com
   Tile 13,https://www.example13.com
   Tile 14,https://www.example14.com
   Tile 15,https://www.example15.com
   Tile 16,https://www.example16.com
   Tile 17,https://www.example17.com
   Tile 18,https://www.example18.com
   Tile 19,https://www.example19.com
   Tile 20,https://www.example20.com
   ```

The list was tested with up to 40 entries, but the tiles should adjust automatically.

## Accessing the Dashboard

Once installed and configured, open a web browser and navigate to the IP address or domain of your server followed by the `/favorites` path. For example:
```
http://your-server-ip/favorites
```
You should now see the responsive dashboard with the tiles displaying the hyperlinks from the `links.csv` file.
