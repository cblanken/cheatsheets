# Splunk

## Misc Notes

- Don't get attached to a particular source type, it's important to corroborate any suspicious activity with multiple source when possible.

## BOTS v1 Example Queries

- Extract password attempt counts

  ```splunk
  index=botsv1 sourcetype=stream:http form_data=*username*passwd* dest_ip=192.168.250.70
  | rex field=form_data "passwd=(?<userpassword>\w+)"
  | stats count by userpassword
  | sort - count
  ```

- Get average length of passwords used in brute force

  ```splunk
  index=botsv1 sourcetype=stream:http http_method=POST
  | rex field=form_data "passwd=(?<userpassword>\w+)"
  | search userpassword=*
  | eval mylen=len(userpassword)
  | stats avg(mylen) as avg_len_http
  | eval avg_len_http=round(avg_len_http,0)
  ```

- Calculate difference (duration) between two events with a `transaction`

  ```splunk
  index=botsv1 sourcetype=stream:http
  | rex field=form_data "passwd=(?<userpassword>\w+)"
  | search userpassword=batman
  | transaction userpassword
  | table duration
  ```

- Calculate unique password attempts

  ```splunk
  index=botsv1 sourcetype=stream:http
  | rex field=form_daa "passwd=(?<userpassword>\w+)"
  | stats dc(userpassword)
  ```

- Identify the name of the file that defaced `imreallynotbatman.com` website with the Fortigate Firewall Events
  ```splunk
  index=botsv1 answer=23.22.63.114 sourcetype=stream:dns | stats values("name{}")
  ```
