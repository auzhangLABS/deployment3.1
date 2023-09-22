## Post- Incident Report

### Report Prepared by: Aubrey Zhang

#### Date and Time of Incident: 9/20/2023 at about 8:00 pm

1. Reason of the Incident:
   - The incident was caused by a new hire that was tasked with updating the URL shortener. The new hire committed to version 2 of the GitHub repository. Since it utilized the webhook, it automatically triggers build, tests, and deploys to the main production server. This replaces the working version 1 with the nonworking version 2

2. Incident Length:
   - Est. 10 mins

3. Steps to resolve the incident:
   - We quickly roll back to the previous working version and push that into the main production server.

4. Incident resolved:
   - The incident has been resolved and we are looking into why version 2 failed.

5. How to prevent it from happening again?
   - We should prevent new hires from getting access to the main production server.
   - Have a chain of command to double check work
