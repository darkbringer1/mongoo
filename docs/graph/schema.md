# GraphQL Schema

This GraphQL schema contains types JobListing, Query, Mutation and input objects CreateJobListingInput, UpdateJobListingInput. It has queries to retrieve job listings such as `jobs` and `job` by supplying an `id`. It also supports creating (`createJobListing`), updating (`updateJobListing`) and deleting (`deleteJobListing`) job listings.

## Types

### JobListing

This type represents a job listing with the following fields:

- `_id` (ID!): Unique identifier of the job listing.
- `title` (String!): Title of the job listing.
- `description` (String!): Description of the job listing.
- `company` (String!): Company of the job listing.
- `url` (String!): URL of the job listing.

### Query

This type has queries to retrieve job listings.

- `jobs: [JobListing!]!`: Retrieves all job listings.
- `job(id: ID!): JobListing!`: Retrieves a job listing by ID.

### Mutation

This type has mutations to create, update and delete job listings.

- `createJobListing(input: CreateJobListingInput!): JobListing!`: Creates a new job listing.
- `updateJobListing(id: ID!, input: UpdateJobListingInput!): JobListing!`: Updates an existing job listing by ID.
- `deleteJobListing(id: ID!): DeleteJobResponse`: Deletes a job listing by ID.

### CreateJobListingInput

Input object for creating a new job listing with the following fields:

- `title` (String!): Title of the job listing.
- `description` (String!): Description of the job listing.
- `company` (String!): Company of the job listing.
- `url` (String!): URL of the job listing.

### UpdateJobListingInput

Input object for updating an existing job listing with the following optional fields:

- `title` (String): Updated title of the job listing.
- `description` (String): Updated description of the job listing.
- `company` (String): Updated company of the job listing.
- `url` (String): Updated URL of the job listing.

### DeleteJobResponse

This type represents the response from the `deleteJobListing` mutation with the following field:

- `deleteJobId` (String!): ID of the deleted job listing.

## Example

### Query

```
query {
  jobs {
    _id
    title
    description
    company
    url
  }
}
```

### Output

```
{
  "data": {
    "jobs": [
      {
        "_id": "job1",
        "title": "Software Engineer",
        "description": "We are hiring for a software engineer...",
        "company": "XYZ Inc.",
        "url": "https://example.com/job1"
      },
      {
        "_id": "job2",
        "title": "Data Analyst",
        "description": "We are seeking a data analyst...",
        "company": "ABC LLC",
        "url": "https://example.com/job2"
      }
    ]
  }
}
```

### Mutation

```
mutation {
  createJobListing(input: {
    title: "DevOps Engineer",
    description: "We are looking for a DevOps engineer...",
    company: "PQR Corp.",
    url: "https://example.com/job3"
  }) {
    _id
    title
    description
    company
    url
  }
}
```

### Output

```
{
  "data": {
    "createJobListing": {
      "_id": "job3",
      "title": "DevOps Engineer",
      "description": "We are looking for a DevOps engineer...",
      "company": "PQR Corp.",
      "url": "https://example.com/job3"
    }
  }
}
```