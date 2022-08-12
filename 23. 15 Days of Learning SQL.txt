select 
submission_date ,

( SELECT COUNT(distinct hacker_id)  
 FROM Submissions s2  
 WHERE s2.submission_date = s1.submission_date AND    (SELECT COUNT(distinct s3.submission_date) FROM      Submissions s3 WHERE s3.hacker_id = s2.hacker_id AND s3.submission_date < s1.submission_date) = dateDIFF(s1.submission_date , '2016-03-01')) ,

(select hacker_id  from submissions s2 where s2.submission_date = s1.submission_date 
group by hacker_id order by count(submission_id) desc , hacker_id limit 1) as shit,
(select name from hackers where hacker_id = shit)
from 
(select distinct submission_date from submissions) s1
group by submission_date