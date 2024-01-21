# Static Website Hosting on AWS with CI/CD Pipeline

## Technologies Covered:
- **AWS Services:**
  - Amazon S3
  - CloudFront
  - Route 53
- **Other Tools:**
  - GitHub
  - Namecheap

## Steps for Implementing this Project:

### S3 Configuration:
1. Create an S3 bucket with a unique name (e.g., `mynameismohan`) and default settings.
2. Edit the bucket settings:
   - Inside the S3 bucket, under properties, edit.
   - Enable static hosting.
   - Specify `index.html` and `error.html` as the default settings.

### CloudFront Configuration:
1. Create a CloudFront distribution:
   - Set the origin domain to the S3 bucket name.
   - Configure origin access with legacy access identities.
   - Create a new OAI (Origin Access Identity) and update the S3 bucket policy accordingly.
   - In the viewer section, enable a policy to redirect HTTP to HTTPS.
   - Allow HTTP methods: GET, HEAD, POST, PUSH.
   - Configure CNAME settings with the S3 bucket name.
   - Request a public SSL certificate.

### Namecheap Configuration:
2. Go to Namecheap and manage the domain.
   - In advanced DNS settings, add a new CNAME record.
   - Type: CNAME, Host: cname_value, Value: cname_value (Copy only the number part from CloudFront CNAME).

### AWS ACM (Amazon Certificate Manager) Configuration:
3. Select the certificate issued by ACM.
   - Set the default root to `index.html`.
   - Create the distribution.

### CodePipeline Configuration:
5. Create a CodePipeline named `s3-deploy`.
   - Set up a new service role.
   - Connect to GitHub using version control.
   - Select the repository containing HTML code.
   - Add webhooks.
   - Skip the build stage.
   - Deploy provider: S3, specify the S3 bucket name.
   - Check the option to extract files before deploying.
   - Create the pipeline.

### CloudFront Cache Management:
8. Manually remove the CloudFront cache after updating the GitHub code.
9. Go to CloudFront, select the distribution, and navigate to invalidations.
   - Add `/*` in the input section to clear the cache across global edge locations.
   - Create invalidations.

This step-by-step guide helps you host a static website on AWS using S3, CloudFront, and Route 53, implementing a CI/CD pipeline with CodePipeline. It also covers DNS configuration on Namecheap and cache management for CloudFront.
