**Generate your seed on linux:**

`cat /dev/urandom |tr -dc A-Z9|head -c${1:-81}`


**Generate your seed on Mac:**

`cat /dev/urandom |LC_ALL=C tr -dc 'A-Z9' | fold -w 81 | head -n 1`


TestNet and Devnet are not working. So the alternative is [comnet](https://comnet.thetangle.org/).



``