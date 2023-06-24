# GraphQL API Model

This code defines the model for a GraphQL API. It contains the following data types:

### 1. CreateJobListingInput Type
This data type represents the input parameters required to create a job listing. It has the following fields:
- `Title` (string) - Title of the job listing
- `Description` (string) - Brief description of the job listing
- `Company` (string) - Company that created the job listing
- `URL` (string) - URL to the job listing

### 2. DeleteJobResponse Type
This data type represents the response returned when a job listing is deleted. It has the following field:
- `DeleteJobID` (string) - ID of the deleted job listing

### 3. JobListing Type
This data type represents a job listing object. It has the following fields:
- `ID` (string) - ID of the job listing
- `Title` (string) - Title of the job listing
- `Description` (string) - Brief description of the job listing
- `Company` (string) - Company that created the job listing
- `URL` (string) - URL to the job listing

### 4. UpdateJobListingInput Type
This data type represents the input parameters required to update a job listing. It has the following fields:
- `Title` (string) - Title of the job listing (optional)
- `Description` (string) - Brief description of the job listing (optional)
- `Company` (string) - Company that created the job listing (optional)
- `URL` (string) - URL to the job listing (optional)

Note: The `omitempty` tag is used with the fields in this data type to indicate that the field is optional.