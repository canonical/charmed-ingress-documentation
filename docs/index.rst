Charmed ingress
==========================

Applications today rarely run in isolation. They need to be reachable by users, other services, or external systems, and they often need control over how traffic enters the deployment.

Charmed ingress solutions provide the traffic layer that makes this possible. They sit at the boundary of your deployment and manage how requests are routed to workloads.

They allow you to:

* Expose your applications outside their network boundary
* Control inbound traffic
* Add routing, security and caching layers
* Standardize access across machine and Kubernetes environments

If your charm workload needs to be reachable from the public internet, a virtual network, or other applications, you will likely need an ingress charm as part of your deployment.

There is no single ingress solution that fits every scenario. The right ingress solution depends on several factors, including:

* Substrate (machine vs Kubernetes)
* Traffic layer (Layer 4 or Layer 7)
* Complexity of ingress requirements
* Security requirements
* TLS termination

To find the right ingress solution for your use case, see :doc:`how-to/choose-an-ingress`.

Have questions?
----------------

Reach out to us on the `Charm Development <https://matrix.to/#/#charmhub-charmdev:ubuntu.com>`_ channel.

.. toctree::
   :hidden:

   how-to/choose-an-ingress
   how-to/contribute
