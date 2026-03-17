.. meta::
    :description: Learn how to identify which charmed ingress solution matches your needs and use case. 

.. _how_to_choose_an_ingress:

Choose the right ingress
========================

Use the following considerations to identify which ingress setup best matches your needs.

Is your workload on a machine or Kubernetes substrate?
------------------------------------------------------

If it's on a machine substrate, the recommended option is the `HAProxy charm <https://github.com/canonical/haproxy-operator>`_.
For Kubernetes, we have the following charms available:

* `Gateway API integrator <https://github.com/canonical/gateway-api-integrator-operator>`_
* `Traefik charm <https://github.com/canonical/traefik-k8s-operator>`_
* `Nginx ingress integrator <https://github.com/canonical/nginx-ingress-integrator-operator>`_

.. note::
   Nginx ingress integrator and Gateway API integrator are workload-less charms and do not install an ingress. The ingress needs to be pre-installed.

Do you require caching?
------------------------

The following charms provide content caching on both machine and Kubernetes substrates:

* `content-cache <https://github.com/canonical/content-cache-operator>`_
* `content-cache-k8s <https://github.com/canonical/content-cache-k8s-operator>`_

Built on top of NGINX, these charms are suited for workloads that serve static assets, documentation, or other repeatable content. Users will benefit from reduced backend traffic and improved response times.

Is your workload charmed? Will your ingress requirements remain static after deployment?
----------------------------------------------------------------------------------------

If your workload is not charmed, or if you expect ingress configuration to change over time, or if you need to configure additional ingress requirements that are not provided by the *ingress* interface, we recommend the `ingress-configurator <https://github.com/canonical/ingress-configurator-operator/>`_ charm. This charm:

* Acts as a translation layer between applications requiring ingress and HAProxy
* Allows non-charmed workloads to integrate into the Juju ecosystem
* Enables dynamic ingress configuration without redeploying infrastructure

Is your traffic on Layer 4 or Layer 7?
--------------------------------------

The kind of traffic that enters your application will influence which ingress solution is appropriate.

* Layer 7 (HTTP/HTTPS) traffic is supported by all ingress charms listed above.
* Layer 4 (TCP) traffic is currently supported only by HAProxy and Traefik.

Choose the right interface
--------------------------

Beyond the core questions above, you may also want to evaluate whether:

* Your ingress is managed per-application or per-unit
* Your requirements are simple or more advanced

The following interfaces are available to be implemented by the ingress requirer charms:

* `Ingress <https://github.com/canonical/traefik-k8s-operator/blob/main/lib/charms/traefik_k8s/v1/ingress.py>`_ - A simple controller-independent interface that provides HTTP/HTTPS routing to an application, including load balancing across all units.
* `Ingress-per-unit <https://github.com/canonical/traefik-k8s-operator/blob/main/lib/charms/traefik_k8s/v1/ingress_per_unit.py>`_ - a simple controller-independent interface that provides an ingress URL per unit.
* \*-route (`haproxy-route <https://github.com/canonical/haproxy-operator/blob/main/haproxy-operator/lib/charms/haproxy/v2/haproxy_route.py>`_, `gateway-route <https://github.com/canonical/gateway-api-integrator-operator/blob/main/gateway-api-integrator/lib/charms/gateway_api/v0/gateway_route.py>`_, `traefik-route <https://github.com/canonical/traefik-k8s-operator/blob/main/lib/charms/traefik_k8s/v0/traefik_route.py>`_, `nginx-route <https://github.com/canonical/nginx-ingress-integrator-operator/blob/main/lib/charms/nginx_ingress_integrator/v0/nginx_route.py>`_) - An advanced alternative to the ingress relation where workload specific configuration can be provided by the user.
