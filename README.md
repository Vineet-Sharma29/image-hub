<p style="text-align:center;"><a href="https://layer5.io/meshery"><img align="left" style="margin-bottom:20px;" src="img/readme/layer5-image-hub.svg"  height="125px" /></a><h1>Layer5 Image Hub</h1></p>

[![Go Report Card](https://goreportcard.com/badge/github.com/layer5io/image-hub)](https://goreportcard.com/report/github.com/layer5io/image-hub)
[![GitHub](https://img.shields.io/github/license/layer5io/image-hub.svg)](LICENSE)
[![GitHub issues by-label](https://img.shields.io/github/issues/layer5io/meshery/help%20wanted.svg)](https://github.com/issues?utf8=✓&q=is%3Aopen+is%3Aissue+archived%3Afalse+org%3Alayer5io+label%3A%22help+wanted%22+")
[![Website](https://img.shields.io/website/https/layer5.io/meshery.svg)](https://layer5.io/)
[![Twitter Follow](https://img.shields.io/twitter/follow/layer5.svg?label=Follow&style=social)](https://twitter.com/intent/follow?screen_name=layer5)
[![Slack](http://slack.layer5.io/badge.svg)](http://slack.layer5.io)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/3564/badge)](https://bestpractices.coreinfrastructure.org/projects/3564)

<p align="center"><i>If you’re using the Image Hub or if you like other Layer5 projects, please <a href="https://github.com/layer5io/image-hub/stargazers">★</a> star this repository to show your support! 🤩</i></p>

## Image Hub
Image Hub is a sample application written to run on [Consul](https://meshery.layer5.io/docs/service-meshes/adapters/consul) for exploring WebAssembly modules used as Envoy filters. This demo application has been enabled by experimental works of [Nic Jackson](https://twitter.com/sheriffjackson) of HashiCorp, and [Kanishkar J](https://twitter.com/_kanishkarj_), [Lee Calcote](https://twitter.com/lcalcote), and other contributors of Layer5.


### Deployment Instructions (pending [meshery-consul/issues/2](https://github.com/layer5io/meshery-consul/issues/2)):

1) Deploy the latest Consul:

```bash
helm repo add hashicorp https://helm.releases.hashicorp.com # Adds helm hashicorp repo
helm install consul hashicorp/consul -f config/consul-values.yaml # Setup custom Consul with support for WASM
```

2) Use [Meshery](https://github.com/layer5io/meshery) to deploy the Image Hub sample application onto the Consul service mesh.

### Use Image Hub

1. Find the port assigned to the `ingess` service:

```
kubectl get svc ingess
NAME     TYPE       CLUSTER-IP    EXTERNAL-IP   PORT(S)        AGE
ingess   NodePort   10.97.34.25   <none>        80:31118/TCP   27m
```

1. Open http://localhost:31118 (where 31118 is your environment's port number).
1. Test your ability to "pull" an image (images are not in fact pulled, but an HTTP request is sent to the backend `api`). You should not be able to pull an image.
1. Sign up a new user and select a subscription plan.
1. Login as that user.
1. Test your ability to "pull" an image. You should be able to pull an image.
1. Open Meshery's performance management page (http://localhost:9081/performance)
1. Configure a performance test against http://x.x.x.x:31118/api/pull (where x.x.x.x is your machine's host IP address, not "localhost")
1. Enter `{ "authorization" : "<your user's token>" }`
1. Run the performance test. See that your subscription plan limit is enforced accordingly.
1. Change your subscription plan and retest.

## Presentations
- [DockerCon 2020](https://docker.events.cube365.net/docker/dockercon/content/Videos/63TCCNpzDC7Xxnm8b) | [deck](https://calcotestudios.com/talks/decks/slides-dockercon-2020-service-meshing-with-docker-desktop-and-webassembly.html)

## Consul Service Mesh Architecture w/WebAssembly
![Service Mesh Architecture - Consul](img/readme/service-mesh-architecture-consul.png)

## Image Hub deployed on Consul
![Meshery and WASM](img/readme/image-hub-on-consul-with-wasm-and-meshery.png)

<div>&nbsp;</div>

## Join the service mesh community!

<a name="contributing"></a><a name="community"></a>
Our projects are community-built and welcome collaboration. 👍 Be sure to see the <a href="https://docs.google.com/document/d/17OPtDE_rdnPQxmk2Kauhm3GwXF1R5dZ3Cj8qZLKdo5E/edit">Meshery Contributors Welcome Guide</a> for a tour of resources available to you and jump into our <a href="http://slack.layer5.io">Slack</a>!

<a href="https://meshery.io/community"><img alt="Layer5 Service Mesh Community" src="img/readme/community.svg" style="margin-left:10px;padding-top:5px;" width="110px" align="right" /></a>

<a href="http://slack.layer5.io"><img alt="Layer5 Service Mesh Community" src="img/readme/slack-128.png" style="margin-right:8px;padding-top:5px;" width="140px" align="left" /></a>

<p>
✔️ <em><strong>Join</strong></em> <a href="https://drive.google.com/open?id=1c07UO9dS7_tFD-ClCWHIrEzRnzUJoFQ10EzfJTpS7FY">community meetings</a>. See details on the <a href="https://calendar.google.com/calendar/b/1?cid=bGF5ZXI1LmlvX2VoMmFhOWRwZjFnNDBlbHZvYzc2MmpucGhzQGdyb3VwLmNhbGVuZGFyLmdvb2dsZS5jb20">Layer5 community calendar</a>.<br />
✔️ <em><strong>Watch</strong></em> community <a href="https://www.youtube.com/channel/UCFL1af7_wdnhHXL1InzaMvA?sub_confirmation=1">meeting recordings</a>.<br />
✔️ <em><strong>Access</strong></em> the <a href="https://drive.google.com/drive/u/4/folders/0ABH8aabN4WAKUk9PVA">community drive</a>.<br />
</p>
<p align="center">
<i>Not sure where to start?</i> Grab an open issue with the <a href="https://github.com/issues?utf8=✓&q=is%3Aopen+is%3Aissue+archived%3Afalse+org%3Alayer5io+label%3A%22help+wanted%22+">help-wanted label</a>.
</p>

<div>&nbsp;</div>

### About Layer5

**Community First**
<p>The <a href="https://layer5.io">Layer5</a> community represents the largest collection of service mesh projects and their maintainers in the world.</p>

**Open Source First**
<p>We build projects to provide learning environments, deployment and operational best practices, performance benchmarks, create documentation, share networking opportunities, and more. Our shared commitment to the open source spirit pushes Layer5 projects forward.</p>

**License**

This repository and site are available as open source under the terms of the [Apache 2.0 License](https://opensource.org/licenses/Apache-2.0).
