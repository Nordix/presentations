---
marp: true
theme: gaia
backgroundColor: #112
class: invert
_footer: 'cdCon | 07.06.2022'
---
<!-- Uses MARP, see https://marp.app/ -->

<!--
class:
 - lead
 - invert
-->

# cdCon 2022

#### Building DevOps metrics for your choice of CD tools through CDEvents

---
# A long long time ago

<!-- Erik

Back in October of 2012 I was working in the telecom industry and I had just gotten involved in one of the early CI/CD efforts in my workplace.

I got my manager to explain the current situation and he said, 
"Well, Erik, to start with we make releases every six months, right?
The development of those releases typically start around a year before release, and the releases get verified by the verification teams during the last three months before release."

So, this means developers frequently need to wait ...
-->

---
# A long long time...

<!-- ... a long long time, like a few months for their work to be fully tested. 
And, of course, it is unlikely that whatever they are working on right now is directly related to what is being verified by the verification team. 

If a bug is discovered, developers need to make the mother of all mental context switches to find and fix the bug. 
Not at all good.

My manager then proclaimed "We need to bring this time, the time from development to verification and release, down from a few months to a few hours."

I remember thinking "going from months to hours seems like a crazy big step!" but I have since been shown over and over again that this step is actually not that crazy!

One factor that really helps taking this step is to understand where our bottlenecks are, and for that we need metrics.

My name is Erik Sternerson...
-->

---
# cdCon 2022

#### Building DevOps metrics for your choice of CD tools through CDEvents

####

####

#### Andrea Frittoli, IBM. Erik Sternerson, doWhile

<!-- Notes

...and my name is Andrea Frittoli.
Welcome to Building DevOps metrics for your choice of CD tools through CDEvents

-->

---
<!--
_class:
 - invert
-->

# In this talk
<!-- Comment
-->

<!-- Notes
Andrea
-->

* ## Learn About CDEvents

* ## Learn About DevOps Metrics

* ## How do they fit together

---

# CDEvents

<!-- Let's first look into what CDEvents is. -->

---

# Conceptual: Common language

<!-- The conceptual goal of the CDEvents project is to help build a common language for CI/CD and surrounding domains.

-->

---

<!--
_class:
 - invert
-->

# Wider effort

<!-- So I set "help build" just now, and that is because this it is not only CDEvents involved in this work. -->

* ## CDF SIG Interoperability

<!-- The Interoperability special interests group of the Continuous Delivery foundation can probably be seen as the "driver" of establishing this common language.

This group does a lot of work defining and establishing terms for similar concepts across the CI/CD ecosystem, and a lot of these terms pop up in the CDEvents project in one way or another.
 -->

* ## CDF SIG Events

<!-- The Events special interest group spawned out of the interoperability group in late 2020 as a workgroup focusing specifically on a vocabulary for events in CI/CD.

It became a full SIG about a year later, and is the root of...
 -->

---

# CDEvents

<!-- The CDEvents project, and its more concrete goal: -->

---

# Concrete: Spec and SDKs

<!-- To build a specification for events in CI/CD, and to build a set of SDKs that help others send and receive such events.
-->

---

![bg contain](images/spec-sdk-poc-1.svg)

<!-- Lets dig in to the spec a bit first. -->

---

![bg contain](images/spec-sdk-poc-1-extra.svg)

<!-- The CDEvents spec declares a number of events that represents things that may happen in CI/CD, such as a change having been merged, a task having been run or a new version of a service having been deployed.

The spec also defines what data can or must be sent for such events, typically data needed by the receivers of the events.

And finally, as CDEvents is based on CloudEvents, the spec also provides rules and guidelines for how to use the attributes provided by the CloudEvents specs, such as source and subject.
-->

---

![bg contain](images/spec-sdk-poc-2.svg)

<!-- Given this spec, we can now work on a set of SDKs for multiple programming languages and platforms. 
-->

---

![bg contain](images/spec-sdk-poc-2-extra.svg)

<!-- So if we want to send an event such as ServiceDeployed in a language for which we have an SDK, we can get quite a lot of help on the way. 
-->

---

![bg contain](images/spec-sdk-poc-3.svg)

<!-- Finally, with the SDKs, we can work on integrating CDEvents into new and existing tools and solutions such as your Jenkinses, Argos, Keptns and Tektons, and set up various proof-of-concepts to test out new ideas and help drive the specification forward. 
-->

---

<!--
_class:
 - invert
-->

# Wider effort (again)

<!-- And this AGAIN is a wider effort. -->

* ## CDEvents team

<!-- The spec itself is driven by the CDEvents team, but with plenty of support, input and feedback from the wider community. 
-->

* ## Project communities

<!-- Several integrations and proof-of-concepts and at least one of the SDKs thus far have been done wholly or partly outside of the CDEvents project itself, by members of the project communities for several CI/CD tools.
-->

---

# What we want to achieve through CDEvents

<!-- Lastly about CDEvents, I want to just very briefly cover the two main areas that we want to address with our project. 

We have covered these desired achievements in way more detail in previous talks, but for the purpose of this talk, our two main goals are... 
-->

---

# Interoperability

<!-- First, interoperability, making things work together by having them speak a common language.
-->

---

# Observability

<!-- And second, and the most relevant for this talk, observability, providing directives both on what to send, as well as when to send it.

Through observability comes a great opportunity for building metrics, and the main focus of our talk today are four major DevOps metrics. 

Andrea, do you want to tell us a bit about those?
-->

---

# DevOps Metrics

<!-- Notes
Thanks Erik for the great introduction about CDEvents.

- Rephrase this, focus on the large DevOps space, fragmented tool landscape
  and seemingly neverending amount on automation work
- Orgs need metrics to know where to invest their work more effectively
- One set of common metrics exists - DORA

The State of the DevOps Report, published by Puppet, has been looking at
how organization implement DevOps over the years. Already since 2013
the report had identified a set of metrics which describe measurable
outcome of organizations implementing DevOps practices.

Andrea
-->

---

<!--
_class:
 - invert
-->

# DORA Metrics

* Deployment Frequency
* Lead Time for Changes
* Change Failure Rate
* Time to Restore Service

<!-- Notes

The four metrics used by the report are those identified by the DORA (DevOps Research and assessment group.
These metrics span the entire software lifecycle. [They do not necessarily cover all aspects of DevOps, and organizations may define other metrics as required.] -> maybe not this last sentence

* Deployment Frequency
* Lead Time for Changes
* Change Failure Rate
* Time to Restore Service

- Depending on the amount of amount of automation, manual or automated
- When automated, a collection of tools and manual inputs contribute to the data

- Advantages of CDEvents:
    - when adopted by tools and individuals, it provides a consistent terminology and data model
    - once the data is collected, easier to process and calculate metrics
    - lower barrier to adopting new tools

Something that is apparent from this list of metrics is that no single tool will produce the data required to calculate them.

Having a common language like CDEvents spoken by different tools would simplify the analysis of data required to calculate the metrics. Our goal is to foster an ecosystem of tools that will be able to do this for systems that can produce CDEvents.

Organizations will be able then to switch one of their tools, or add a new one, and as long as it supports CDEvents, metrics will keep working.

Andrea
-->

---

# Metrics through CDEvents

<!-- Notes

EriK: Ok, with that excellent recap from Andrea on the four metrics we are
talking about today, lets move on to looking at how CDEvents can help
establish these metrics.

Erik
-->

---

# Deployment Frequency

<!-- Erik

The first one, which may be the most straightforward one, is Deployment Frequency.
-->

---

![bg contain](images/depfreq-1.svg)

<!-- Say that we have this pretty simple setup with an orchestrator helping us deploy our application to an environment.

This orchestrator could be many things, for instance kubectl controlled via Tekton, or some other DevOps automation tools like ArgoCD or Spinnaker or Keptn.
 -->

---

![bg contain](images/depfreq-2.svg)

<!-- Anyway, say that we have a new version of our application coming in.

We want to upgrade our existing deployment, and maybe we've also made a configuration change to state that we want an additional deployment in a new environment. -->

---

![bg contain](images/depfreq-3.svg)

<!-- In CDEvents, we have two events to cover both these cases, ServiceUpgraded and ServiceDeployed. -->

---

![bg contain](images/depfreq-4.svg)

<!-- Given that the events state both what was deployed or upgraded, and to what new version, and to what environment, these events are sufficient for an observer to be able to detect how often new versions are deployed, and would thus be able to produce the Deployment Frequency metric.
-->

---

# Lead Time for Changes

<!-- Notes

The lead time for changes considers data that spans from the SCM system down to the deployment one.

Andrea
-->

---

![bg contain](images/cdevents-lead-time-for-changes.svg)

<!--  Notes

Starting with the SCM, regardless of the tool we use, there will be a concept of repository which must be part of any Change related event in CDEvents. The timestamp of the change a second mandatory piece of information.

Let's for now assume a single artifact, single branch scenario.

-->

---

![bg contain](images/cdevents-lead-time-for-changes-build.svg)

<!--  Notes

The build system creates an artifact from a subset of the changes merged into the SCM. If we could assume a monotonic relation over time between changes and build, repository and timestamp would be enough to know which change is included in which build.
In most cases though we will need to consider change IDs, and expect Artifact events to include the last change ID included in the build.
To discover if a change is included in a build, the observer will need to ask the SCM if a change ID was merged "before" the last change ID included in the build.

-->

---

![bg contain](images/cdevents-lead-time-for-changes-deploy.svg)

<!--  Notes

The build system may use different tools depending on the type of artifact and on the preferences of the team responsible for it. In all cases the build process must outcome an artifact ID which uniquely identifies the artifact. This ID is used by the deployment system to obtain the artifact to deploy, and is then reported back in the Service replated CDEvents.

We started with the single artifact scenario, however in real life, we will often need to consider composition scenarios, where an artifact is not directly deployed, but it's used instead to build a composite artifact or collection of artifacts (release).

We started investigating how to define such scenarios in CDEvents,
exploring the idea of composition.

-->

---

# Change Failure Rate

<!-- The next metric, Change Failure Rate, is an interesting one from an events perspective, so lets look into that.
-->

---

# # Deployments / # Incidents

<!-- This metric can be simplified as the number of deployments we have over the number of incidents that occur for these deployments. -->

---

![bg contain](images/depfreq-4.svg)

<!-- Counting he number of deployments is actually pretty straightforward using the ServiceDeployed and ServiceUpgraded events we looked at earlier.

Not much to worry about there, so lets have a look at incidents.
 -->

---

# Incidents

<!-- Counting incidents is a bit more involved. -->

---
<!--
_class:
 - invert
-->

# What can cause an incident?

<!-- First of all, incidents may have many different causes. -->

* ## Application error (bug!)

<!-- It could be a bug in the application or service we are deploying. -->

* ## Configuration error

<!-- It could be a mistake in the configuration of the application. -->

* ## Environment error

<!-- It could also be something entirely unrelated to the application itself,such as a network outage or other type of environment errors. -->

* ## ...

<!-- And the list of causes doesn't stop there. -->

---
<!--
_class:
 - invert
-->

# Who can discover an incident?

<!-- Given the variety of causes of incidents, there will also be many different sources that can discover these issues. -->

* ## Orchestrator

<!-- The system that deploys your application may notice that it doesn't come up properly after deployment. -->

* ## Monitoring system

<!-- A monitoring system may detect that your application har degraded performance -->

* ## Application itself

<!-- Of course the application itself may discover that it is not doing well -->

* ## Users / DevOps team

<!-- There may even be manual reports by users or some operations team, maybe into a bugtracker or similar. 

Given that we have so many possible sources, what can should be done when an incident is discovered? -->

---

# Send an Incident event!

<!-- We send an Incident event!

Now, this event type is new for us, in fact it hasn't formally made it into the spec yet, but we have some prior art which Andrea will mention a bit later. -->

---

![bg contain](images/cfr-1.svg)

<!-- Anyway, given the same deployment we saw before, with an orchestrator and this time also a monitor (like Prometheus)/ -->

---

![bg contain](images/cfr-2.svg)

<!-- We could have Incidents reported by the orchestrator ... -->

---

![bg contain](images/cfr-3.svg)

<!-- ... by the monitoring system ... -->

---

![bg contain](images/cfr-4.svg)

<!-- ... and by the application itself ... -->

---

![bg contain](images/cfr-5.svg)

<!-- ... and from users or the operations team. -->

---

![bg contain](images/cfr-6.svg)

<!-- But all of these could be seen by an observer which could then determine the total number of incidents and produce the desired metric. -->

---

# Time to Restore Service

---
<!--
_class:
 - invert
-->

# What can restore the service?

* ## A rollback or deployment of a newer version
* ## Configuration change (e.g. scaling)
* ## A change to an external dependency

<!-- Note

A service degradation may be solved in a number of ways:
- a rollback or the deployment of a newer version
- scaling, horizontally or vertically
- a change external to the system that suffered the degradation (another microservice, networking issues, etc)

As Erik mentioned, incident events are not part of CDEvents yet. Given the number of possible different scenarios, having dedicated incident and incident resolution events is required to calculate the time to restore service metric.
Data The environment and the service identifiers and the version deployed must be part of all incident resolution events, along with the original incident ID.
The time to restore service may be or may be not associated with a change in the system, thus the related data will be optional in the events.

-->
---

# Keptn Application Lifecycle Events

<!-- Note

Keptn provides abstractions, automation and events related to SLIs, SLOs and
problems. That enables generating events valuable for tracking the time to
restore service metric. The CDEvents project is evaluating whether to adopt
the Keptn model for its own application lifecycle type of events.

-->

---

# Who generate the incident resolution events

<!-- Note

Who generate the incident resolution events?
Different systems may send events about the same incident resolution, with different amount of context. We plan to allow multiple events in this area that can be collated later by the observer.

Andrea
-->

---

![bg contain](images/ttrs-1.svg)

<!-- Notes

Events from the orchestrator.

For instance, when using Knative, a service may be scaled up and down based on metrics. A metric degradation that leads to scaling up could generate the incident event, and the Knative autoscaler could send CDEvents about the incident resolution once the scaling up is done.

Andrea
-->

---

![bg contain](images/ttrs-2.svg)
<!-- Notes

Events from the monitoring system

Andrea
-->

---

![bg contain](images/ttrs-3.svg)
<!-- Notes

Events from the application or a human

In many instances the resolution may not be automated at all. The CDEvents SDKs may be used to provide a workflow for engineers to record the data
required to keep track of the "time to restore service". This could be integrated for instance in the issue tracking system of choice.

Andrea
-->

---

# Key takeaways

<!-- Erik

We're nearing the end of the talk, so let's wrap up with a few key takeaways. -->

---

# Metrics are tricky

<!-- As we've talked about, metrics may require several different pieces of information, and these pieces may come from many different sources ... -->

---

# Metrics are tricky

![bg contain](images/key-takeaway-1.svg)

<!-- ... so bringing all this together to produce the desired metrics can be really tricky. -->

---

# A common language helps!

![bg contain](images/key-takeaway-1.svg)

<!-- Having then a common language and a standardized way of distributing information in this common language can really help ... -->

---

# A common language helps!

![bg contain](images/key-takeaway-2.svg)

<!-- ... and this is the aim of the CDEvents project. -->

---

# A call to action

<!-- And to make this possible, the CDEvents project and community can
really benefit from your involvement, in anything ranging from giving
feedback and providing your use cases, to working with us on the spec
or developing SDKs and integrations. -->

---

# cdevents.dev

<!-- You can find our work, and how to get involved, on cdevents.dev -->

---

# Thank you!

<!-- With that, we'd like to thank you all for attending the talk,
I've been Erik Sternerson, this is Andrea Frittoli, and we'd now
like to open the floor for questions. -->

---
<!--
_footer: 'cdCon | 07.06.2022'
-->

# Questions?

##
##
##
##
##

#### Andrea Frittoli, IBM. Erik Sternerson, doWhile
