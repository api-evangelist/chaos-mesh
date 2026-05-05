---
title: "Chaos Mesh Q&A at KUBECON EU 2022"
url: "https://chaos-mesh.org/blog/chaos-mesh-qa-at-kubecon-eu-2022/"
date: "Tue, 07 Jun 2022 00:00:00 GMT"
author: ""
feed_url: "https://chaos-mesh.org/blog/rss.xml"
---
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh Q&amp;amp;A" class="img_hi9z" height="1043" src="https://chaos-mesh.org/assets/images/chaos-mesh-q&amp;a-5ee3460631a40ccb4ab675860e9bddd7.jpeg" width="3126" /><figcaption class="text--italic text--center">Chaos Mesh Q&amp;A</figcaption></figure><p></p>
<p>At KubeCon EU 2022, the <a class="" href="https://chaos-mesh.org/" rel="noopener noreferrer" target="_blank">Chaos Mesh</a> team hosted two activities "Make Cloud Native Chaos Engineering Easier - Deep Dive into Chaos Mesh" and "office hours session". We are very grateful and enjoyed it with all of you very much. We shared with each other, got to know each other, and discussed a lot of things in depth.</p>
<!-- -->
<p>For the presentations, we gave a brief overview of Chaos Mesh, then delved into how Chaos Mesh is implemented and how it is practiced, and shared the team's latest explorations around chaos engineering and plans for Chaos Mesh's development.</p>
<p>For Office Hour, we introduced the Chaos Mesh project and its latest progress, and answered online questions from attendees.</p>
<p>Many thanks to each of our friends that came out to support us! And for Office Hour, we received some great questions and we decided to have a follow-up Q&amp;A.</p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="your-questions-answered">Your questions answered<a class="hash-link" href="https://chaos-mesh.org/blog/chaos-mesh-qa-at-kubecon-eu-2022/#your-questions-answered" title="Direct link to Your questions answered">​</a></h2>
<p><strong>Q: Does chaos play well with Windows/Linux hybrid clusters?</strong></p>
<p><strong>A:</strong> Chaos Mesh can only work with Linux now, but we have kindly contributors who are trying to port some features to Windows: <a class="" href="https://github.com/chaos-mesh/chaos-mesh/issues/2956" rel="noopener noreferrer" target="_blank">github.com/chaos-mesh/chaos-mesh/issues/2956</a></p>
<p><strong>Q: I think Istio and Linkerd also support fault injection. How does Chaos Mesh differ? Chaos Mesh provides much richer chaos injections (like IOChaos, TimeChaos...), but the injection provided by linked or istio, as I know, is focused on the network?</strong></p>
<p><strong>A:</strong> Yeah of course! Service Mesh Frameworks have the potential to cause havoc in the RPC/Network layer. More types of chaos, such as stresschaos, pod kill, DNSChaos, and IOChaos, could be injected into Chaos Mesh (just mentioned) In addition to the list, we offer additional types of chaos. JVM, GCP, Azure, and so on...</p>
<p><strong>Q: As part of the chaos mesh can we run any pre-initialization scripts before introducing the chaos experiment?</strong></p>
<p><strong>A:</strong> Yes! You may organize your customized scripts and various chaotic experiments together with Chaos Mesh's integrated Workflow engine. See <a class="" href="https://chaos-mesh.org/docs/next/create-chaos-mesh-workflow/#task-field-description" rel="noopener noreferrer" target="_blank">task field in workflow</a> for the document.</p>
<p><strong>Q: Is this similar to the Gremlin Chaos engineering tool?</strong></p>
<p><strong>A:</strong> Yes, this is a Kubernetes-specific open-source project. It's a Kubernetes plugin that you can utilize. You can get more Infos on <a class="" href="https://chaos-mesh.org/" rel="noopener noreferrer" target="_blank">https://chaos-mesh.org</a></p>
<p><strong>Q: How does it inject network latency for network chaos? if we use cilium CNI with no iptables, would this latency injection still work in that case?</strong></p>
<p><strong>A:</strong> Chaos Mesh has a chaos-daemon component. When network chaos is produced, chaos-daemon will enter the target pod's network namespace and set TC and iptables rules on the network device.</p>
<p>When using clium CNI without iptables, Chaos Mesh still works.</p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="join-the-chaos-mesh-community">Join the Chaos Mesh community<a class="hash-link" href="https://chaos-mesh.org/blog/chaos-mesh-qa-at-kubecon-eu-2022/#join-the-chaos-mesh-community" title="Direct link to Join the Chaos Mesh community">​</a></h2>
<p>If you are interested in Chaos Mesh and would like to help us improve it, you're welcome to join <a class="" href="https://slack.cncf.io/" rel="noopener noreferrer" target="_blank">our Slack channel</a>(#project-chaos-mesh) or submit your pull requests or issues to our <a class="" href="https://github.com/chaos-mesh/chaos-mesh" rel="noopener noreferrer" target="_blank">GitHub repository</a>.</p>
