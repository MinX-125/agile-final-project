# Agile Final Project - Product Backlog User Stories

## 1. Need the ability to create a product in the catalog

**Label:** enhancement
**Priority:** High

**As a** user
**I need** a service that allows me to create a product in the catalog
**So that** new products can be added and made available.

### Details and Assumptions

* The product should include basic details such as name, description, price, and category.
* Required product fields must be validated before saving.
* Each product should receive a unique product ID.
* Invalid product creation requests should return an error message.

### Acceptance Criteria

```gherkin
Given I provide valid product details
When I make a request to create a product
Then the product should be added to the catalog
And a unique product ID should be returned
```

```gherkin
Given I provide missing or invalid product details
When I make a request to create a product
Then the product should not be created
And an error message should be returned
```

---

## 2. Need the ability to retrieve a product from the catalog

**Label:** enhancement
**Priority:** High

**As a** user
**I need** a service that allows me to retrieve a product from the catalog
**So that** I can view product details when needed.

### Details and Assumptions

* A product should be retrievable using its product ID.
* The service should return all stored details for the product.
* If the product does not exist, the service should return a proper not-found response.

### Acceptance Criteria

```gherkin
Given a product exists in the catalog
When I make a request to retrieve the product using its product ID
Then the product details should be returned
```

```gherkin
Given a product does not exist in the catalog
When I make a request to retrieve the product using its product ID
Then a product not found message should be returned
```

---

## 3. Need the ability to update a product in the catalog

**Label:** enhancement
**Priority:** High

**As a** user
**I need** a service that allows me to update a product in the catalog
**So that** product information can stay accurate.

### Details and Assumptions

* Only existing products should be updated.
* The user should be able to update product details such as name, description, price, and category.
* Invalid update requests should be rejected.
* The latest updated product details should be returned after a successful update.

### Acceptance Criteria

```gherkin
Given a product exists in the catalog
When I make a request with valid updated product details
Then the product should be updated in the catalog
And the updated product details should be returned
```

```gherkin
Given a product does not exist in the catalog
When I make a request to update the product
Then the product should not be updated
And a product not found message should be returned
```

---

## 4. Need the ability to delete a product from the catalog

**Label:** enhancement
**Priority:** High

**As a** user
**I need** a service that allows me to delete a product from the catalog
**So that** products that are no longer needed can be removed.

### Details and Assumptions

* A product should be deleted using its product ID.
* Only existing products should be deleted.
* Once deleted, the product should no longer be available in the catalog.
* If the product does not exist, the service should return a proper not-found response.

### Acceptance Criteria

```gherkin
Given a product exists in the catalog
When I make a request to delete the product
Then the product should be removed from the catalog
And it should no longer be returned in future requests
```

```gherkin
Given a product does not exist in the catalog
When I make a request to delete the product
Then a product not found message should be returned
```

---

## 5. Need the ability to Like a product in the catalog

**Label:** enhancement
**Priority:** Medium

**As a** user
**I need** a service that allows me to like a product in the catalog
**So that** I can show positive interest in a product.

### Details and Assumptions

* A product should be liked using its product ID.
* The product must exist before it can be liked.
* The like count should increase when the product is liked.
* The updated like count should be returned.

### Acceptance Criteria

```gherkin
Given a product exists in the catalog
When I make a request to like the product
Then the product like count should increase by 1
And the updated like count should be returned
```

```gherkin
Given a product does not exist in the catalog
When I make a request to like the product
Then the like count should not be updated
And a product not found message should be returned
```

---

## 6. Need the ability to Dislike a product in the catalog

**Label:** enhancement
**Priority:** Medium

**As a** user
**I need** a service that allows me to dislike a product in the catalog
**So that** I can show negative interest in a product.

### Details and Assumptions

* A product should be disliked using its product ID.
* The product must exist before it can be disliked.
* The dislike count should increase when the product is disliked.
* The updated dislike count should be returned.

### Acceptance Criteria

```gherkin
Given a product exists in the catalog
When I make a request to dislike the product
Then the product dislike count should increase by 1
And the updated dislike count should be returned
```

```gherkin
Given a product does not exist in the catalog
When I make a request to dislike the product
Then the dislike count should not be updated
And a product not found message should be returned
```

---

## 7. Need the ability to list all products in the catalog

**Label:** enhancement
**Priority:** Medium

**As a** user
**I need** a service that allows me to list all products in the catalog
**So that** I can view every product currently available.

### Details and Assumptions

* Need a way to retrieve all products.
* The response should include product details.
* If no products exist, an empty list should be returned.
* The list should be consistent with the current catalog data.

### Acceptance Criteria

```gherkin
Given products exist in the catalog
When I make a request to list all products
Then all available products should be returned
```

```gherkin
Given no products exist in the catalog
When I make a request to list all products
Then an empty list should be returned
```

---

## 8. Need the ability to query a subset of products in the catalog

**Label:** enhancement
**Priority:** Medium

**As a** user
**I need** a service that allows me to query a subset of products in the catalog
**So that** I can find products based on specific criteria.

### Details and Assumptions

* Need a way to filter products.
* Query may support fields such as name, category, price, or availability.
* Only matching products should be returned.
* If no products match, an empty list should be returned.

### Acceptance Criteria

```gherkin
Given products exist in the catalog
When I make a request with query parameters
Then only the products matching the query should be returned
```

```gherkin
Given no products match the query parameters
When I make a request to query products
Then an empty list should be returned
```

---

## 9. Must be hosted in the cloud

**Label:** technical debt
**Priority:** High

**As a** user
**I need** the catalog service to be hosted in the cloud
**So that** it can be accessed reliably from anywhere.

### Details and Assumptions

* The service should be deployed to a cloud platform.
* The application should be reachable through a public URL.
* The cloud environment should support the required runtime and database.
* The service should remain available after deployment.

### Acceptance Criteria

```gherkin
Given the service has been deployed to the cloud
When I access the public service URL
Then the catalog service should be available
And it should respond to valid API requests
```

---

## 10. Must have automation to deploy new changes to the cloud

**Label:** technical debt
**Priority:** High

**As a** user
**I need** automation to deploy new changes to the cloud
**So that** updates can be released faster and with fewer manual steps.

### Details and Assumptions

* Need a CI/CD pipeline.
* Deployment should trigger when new changes are pushed.
* Automated tests should run before deployment.
* Failed builds should not be deployed.
* Successful builds should be deployed to the cloud environment.

### Acceptance Criteria

```gherkin
Given a new code change is pushed to the repository
When the deployment pipeline runs successfully
Then the latest changes should be deployed to the cloud
And the cloud service should reflect the new version
```

```gherkin
Given a new code change causes the pipeline to fail
When the deployment pipeline runs
Then the failed build should not be deployed to the cloud
```

