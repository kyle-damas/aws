# Search AWS Documentation
**Issue:** My customer was waiting for the next Aurora PostgreSQL patch release as it included an important fix for them.  
**Solution:** I created a Lambda that searches the URL for specific text and will publish to a SNS topic when the text is found. I scheduled it to run each morning (8 AM CST, which is 13:00 UTC) via EventBridge. I subscribed my phone number to the SNS topic, so I'll receive a text once found.

The [CloudFormation template](https://github.com/kyle-damas/aws/blob/main/search-aws-documentation/search-aws-documentation.yaml) requires the following input parameters:  
- URL -> The URL that you want to search for specific text.
- SearchTerm -> The string that you want to search in that URL.
- SNSTopic -> The ARN for the SNS topic where a message will be published once the text is found on that URL.
