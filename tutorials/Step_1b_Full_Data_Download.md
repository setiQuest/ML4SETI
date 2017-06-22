## Getting the Full Dataset the "Ninja Way" ##

Download the csv file of all urls, and then use xargs to run parallel downloaders
Adjust the -P flag in xargs for thread count. At 100 threads on a university connection, downloading all 140k files should take 15 minutes.

~~~
> mkdir dataset
> cd dataset
> wget https://dal.objectstorage.open.softlayer.com/v1/AUTH_cdbef52bdf7a449c96936e1071f0a46b/simsignals_files/public_list_primary_v3_full_21june_2017.csv
> cat public_list_primary_v3_full_21june_2017.csv | grep -v UUID | cut -d ',' -f 1 | awk '{printf("https://dal.objectstorage.open.softlayer.com/v1/AUTH_cdbef52bdf7a449c96936e1071f0a46b/simsignals_v3/%s.dat\n",$1)}' > full-urls
> cat full-urls | xargs -n 1 -P 100 wget -q
~~~
