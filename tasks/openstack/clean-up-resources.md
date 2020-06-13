# Always cleanup cloud resources after you're done

It's always a good idea to delete/remove any **unwanted** cloud resources; as long as you're sure you don't need them.

When deleting resources you have to follow a certain order. Typically you delete/remove things in the reverse order of how you created them.

For example, we should typically shutdown and delete the instances first but if there are storage volumes attached to the instance then you should detach the volumes before deleting the instances. Simiarly, if a router has interfaces on it beyond the gateway ones, then delete the interfaces on the router(s), before deleting the router(s). Deleting a router with existing interfaces will not work.... and so on.

*In general*, do the following in order listed. **Not all steps may apply to you depending on your setup**

1. Detach secondary storage volumes if present (these may also be deleted if not needed)
2. Shutdown the instance(s)
3. Delete the instance (s)
4. Delete each of the interfaces on your router (don't have to delete the gateway interface separately, it should get deleted when deleting the router)
5. Delete the router itself
6. Delete the network you created (you may have to ensure you delete all ports on this network first if you get an error message when trying to delete the network)