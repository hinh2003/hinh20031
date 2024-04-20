https://hortonassets.s3.amazonaws.com/tutorial/hive/Twitterdata.txt

Dữliệubaogồmcáctrườngnhư:id,username,content,timestamp,location,retweet_count,vàfavorite_count.
SELECT username, 
       SUM(retweet_count) AS total_retweets, 
       SUM(favorite_count) AS total_favorites
FROM giao_dich
GROUP BY username;
