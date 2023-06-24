# MongoDB Database Connection and Operations

This code is a Go package to connect to a MongoDB database and perform operations like get, create, update, or delete job listings. 

## Functions

### Connect()

This function is used to connect to the MongoDB database. It returns a DB object which is used to perform various operations on the database. 

### GetJob(id string) *model.JobListing 

This function takes in a string parameter as ID and returns a pointer to a JobListing model. It is used to get the job listing from the database based on its ID.

### GetJobs() []*model.JobListing 

This function returns a slice of pointers to JobListing models. It is used to get all the job listings from the database.

### CreateJobListing(jobInfo model.CreateJobListingInput) *model.JobListing 

This function takes a job listing object as input and returns a pointer to a JobListing model. It is used to create a new job listing in the database.

### UpdateJobListing(jobId string, jobInfo model.UpdateJobListingInput) *model.JobListing 

This function takes in a string parameter as job ID and a job listing object as input and returns a pointer to a JobListing model. It is used to update an existing job listing in the database.

### DeleteJobListing(jobId string) *model.DeleteJobResponse 

This function takes in a string parameter as job ID and returns a pointer to a DeleteJobResponse model. It is used to delete an existing job listing from the database.

## Usage

```go
package main

import (
	"log"

	"github.com/darkbringer1/mongoo/database"
	"github.com/darkbringer1/mongoo/graph/model"
)

func main() {
	db := database.Connect()

	// Get a job listing by id
	job := db.GetJob("60f2ec8a8087df13f2a2cf3f")
	log.Println(job)

	// Get all job listings
	jobs := db.GetJobs()
	log.Println(jobs)

	// Create a new job listing
	newJob := model.CreateJobListingInput{
		Company:        "New Company",
		Position:       "New Position",
		Description:    "New Description",
		Email:          "test@test.com",
		Location:       "New Location",
		Experience:     "New Experience",
		Salary:         "New Salary",
		JobType:        "New JobType",
		Published_date: "New Published Date",
	}
	createdJob := db.CreateJobListing(newJob)
	log.Println(createdJob)

	// Update an existing job listing
	updateJob := model.UpdateJobListingInput{
		Company:        "Updated Company",
		Position:       "Updated Position",
		Description:    "Updated Description",
		Email:          "test@test.com",
		Location:       "Updated Location",
		Experience:     "Updated Experience",
		Salary:         "Updated Salary",
		JobType:        "Updated JobType",
		Published_date: "Updated Published Date",
	}
	updatedJob := db.UpdateJobListing("60f2ec8a8087df13f2a2cf3f", updateJob)
	log.Println(updatedJob)

	// Delete a job listing by id
	response := db.DeleteJobListing("60f2ec8a8087df13f2a2cf3f")
	log.Println(response)
}
```