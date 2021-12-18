# Never under-estimate a seemingly easy looking piece of work:

Recently I had worked on some changes, as part of this we had to remove the existing proxy and needed to replace it with endpoints.  
For ex:
```python
# existing changes:
boto3.client('kms', http_proxy='http://<host>:<port>')
# or,
boto3.client('sqs', http_proxy='http://<host>:<port>')
# or, 
boto3.client('ses', http_proxy='http://<host>:<port>')
# etc.
```

Now, the requirement was to remove the proxy usage and replace it with endpoint_urls.  
For ex:
```python
boto3.client('kms', endpoint_url='http://<kms_endpoint>')

# or,
boto3.client('sqs', endpoint_url='http://<sqs_endpoint>')
# or, 
boto3.client('ses', endpoint_url='http://<ses_endpoint>')
# etc.
```

A piece of work looking as simple as the above gave me a hard time, I had several `non-technical learnings` as follows:  

1. We must analyze the scope of work:
   and if it is project wide changes, then generally ask for a whole sprint of development work, excluding buffers,  
2. Analyze the code changes as well, for ex: as per the requirement,  
   it says only for boto3.client(..) calls but the same could be very much applicable the service is being invoked from other methods like aws cli, aws sdk api etc.  
3. If there are many-more changes, there are high chances of unintentional misses or gaps,
4. It will require a good review efforts,
5. Supporting to QA across all env, (dev/stg/prd),
6. There could be chances of new surprises during the work,
7. May require co-ordination with DevOps or support from other depending teams,
8. Also, analyze on the # of resources required for the work
9. we also need to consider how much is the existing code quality,  
  if it is not well designed by following good practices, then believe me, navigating through it will be very-2 hard.  
  which is a subtle overhead often gets unnoticed  

Hence, we must prepare and consider all the above points while estimating a story!  
so, I'd estimate to be 2 sprints work (i.e. 1 month for the end-2-end delivery till production env.)  

