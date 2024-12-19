# API Resources

## Naming Resources

- Resources should have singular names, reflecting the Eloquent model they represent, e.g., UserResource.
- Resource collections should use `collection` suffix after the model name, e.g., UserCollection.

## Resources for Different User Types

- Maintain Multiple Resources for a Model: This ensures modularity and clear data-access boundaries. For example, a ConsumerOrderResource, StorekeeperOrderResource, and CourierOrderResource for the Order Model.
- Namespaced URLs: Utilize namespaced URLs to differentiate data meant for separate User Types. For example, `/consumers/id/orders/id` and `/couriers/id/orders/id`.
- Embed Data-Access Policies: Implementing data-access policies within the resource layer ensures inherent data privacy. For example, a `CourierOrderResource` should not return the data related to consumers or storekeepers only.

