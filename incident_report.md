## Post- Incident Report

### Report Prepared by: Aubrey Zhang

#### Date and Time of Incident: 9/20/2023 at approximately 8:00 pm

#### Reason for the Incident:
   - The incident was caused by a deployment error during an update to the URL shortener application. A new hire updated the URL shorter, committing changes within the URL shortener application to the GitHub repository. This act triggers a build and deploy process with Jenkins, that replaces the working version with the nonworking version.

#### Incident Length:
   - Approximately. 10 mins
   - Temporary disruption in the URL shortener service

#### Steps to resolve the incident:
   - Quicky, rolled back to the previous version of the URL shortener.
   - Start an investigation into the root cause of Version 2 failure.

#### Incident resolved:
   - The incident has been resolved, with services restored back to working version 1.

#### How to prevent it from happening again?
   - Implement control policies to limit access to production servers, especially for new hires.
   - Establish a chain of command to set a peer review process for critical deployments.
   - Ensure deployment works within the staging environment through testing.
