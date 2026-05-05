---
title: "Chaos Mesh + SkyWalking: Better Observability for Chaos Engineering"
url: "https://chaos-mesh.org/blog/better-observability-for-chaos-engineering/"
date: "Thu, 16 Dec 2021 00:00:00 GMT"
author: ""
feed_url: "https://chaos-mesh.org/blog/rss.xml"
---
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh + SkyWalking: Better Observability for Chaos Engineering" class="img_hi9z" height="501" src="https://chaos-mesh.org/assets/images/chaos-mesh-skywalking-banner-1f6183766d34f1bcd35f2e812504954f.png" width="1501" /><figcaption class="text--italic text--center">Chaos Mesh + SkyWalking: Better Observability for Chaos Engineering</figcaption></figure><p></p>
<p><a class="" href="https://github.com/chaos-mesh/chaos-mesh" rel="noopener noreferrer" target="_blank">Chaos Mesh</a> is an open-source cloud-native <a class="" href="https://en.wikipedia.org/wiki/Chaos_engineering" rel="noopener noreferrer" target="_blank">chaos engineering</a> platform. You can use Chaos Mesh to conveniently inject failures and simulate abnormalities that might occur in reality, so you can identify potential problems in your system. Chaos Mesh also offers a Chaos Dashboard which allows you to monitor the status of a chaos experiment. However, this dashboard cannot let you observe how the failures in the experiment impact the service performance of applications. This hinders us from further testing our systems and finding potential problems.</p>
<!-- -->
<p><a class="" href="https://github.com/apache/skywalking" rel="noopener noreferrer" target="_blank">Apache SkyWalking</a> is an open-source application performance monitor (APM), specially designed to monitor, track, and diagnose cloud native, container-based distributed systems. It collects events that occur and then displays them on its dashboard, allowing you to observe directly the type and number of events that have occurred in your system and how different events impact the service performance.</p>
<p>When you use SkyWalking and Chaos Mesh together during chaos experiments, you can observe how different failures impact the service performance.</p>
<p>This tutorial will show you how to configure SkyWalking and Chaos Mesh. You’ll also learn how to leverage the two systems to monitor events and observe in real time how chaos experiments impact applications’ service performance.</p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="preparation">Preparation<a class="hash-link" href="https://chaos-mesh.org/blog/better-observability-for-chaos-engineering/#preparation" title="Direct link to Preparation">​</a></h2>
<p>Before you start to use SkyWalking and Chaos Mesh, you have to:</p>
<ul>
<li class="">Set up a SkyWalking cluster according to <a class="" href="https://github.com/apache/skywalking-kubernetes#install" rel="noopener noreferrer" target="_blank">the SkyWalking configuration guide</a>.</li>
<li class="">Deploy Chao Mesh <a class="" href="https://chaos-mesh.org/docs/production-installation-using-helm/" rel="noopener noreferrer" target="_blank">using Helm</a>.</li>
<li class="">Install <a class="" href="https://jmeter.apache.org/index.html" rel="noopener noreferrer" target="_blank">JMeter</a> or other Java testing tools (to increase service loads).</li>
<li class="">Configure SkyWalking and Chaos Mesh according to <a class="" href="https://github.com/chaos-mesh/chaos-mesh-on-skywalking" rel="noopener noreferrer" target="_blank">this guide</a> if you just want to run a demo.</li>
</ul>
<p>Now, you are fully prepared, and we can cut to the chase.</p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="step-1-access-the-skywalking-cluster">Step 1: Access the SkyWalking cluster<a class="hash-link" href="https://chaos-mesh.org/blog/better-observability-for-chaos-engineering/#step-1-access-the-skywalking-cluster" title="Direct link to Step 1: Access the SkyWalking cluster">​</a></h2>
<p>After you install the SkyWalking cluster, you can access its user interface (UI). However, no service is running at this point, so before you start monitoring, you have to add one and set the agents.</p>
<p>In this tutorial, we take Spring Boot, a lightweight microservice framework, as an example to build a simplified demo environment.</p>
<ol>
<li class="">Create a SkyWalking demo in Spring Boot by referring to <a class="" href="https://github.com/chaos-mesh/chaos-mesh-on-skywalking/blob/master/demo-deployment.yaml" rel="noopener noreferrer" target="_blank">this document</a>.</li>
<li class="">Execute the command <code>kubectl apply -f demo-deployment.yaml -n skywalking</code> to deploy the demo.</li>
</ol>
<p>After you finish deployment, you can observe the real-time monitoring results at the SkyWalking UI.</p>
<p><strong>Note:</strong> Spring Boot and SkyWalking have the same default port number: 8080. Be careful when you configure the port forwarding; otherise, you may have port conflicts. For example, you can set Spring Boot’s port to 8079 by using a command like <code>kubectl port-forward svc/spring-boot-skywalking-demo 8079:8080 -n skywalking</code> to avoid conflicts.</p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="step-2-deploy-skywalking-kubernetes-event-exporter">Step 2: Deploy SkyWalking Kubernetes Event Exporter<a class="hash-link" href="https://chaos-mesh.org/blog/better-observability-for-chaos-engineering/#step-2-deploy-skywalking-kubernetes-event-exporter" title="Direct link to Step 2: Deploy SkyWalking Kubernetes Event Exporter">​</a></h2>
<p><a class="" href="https://github.com/apache/skywalking-kubernetes-event-exporter" rel="noopener noreferrer" target="_blank">SkyWalking Kubernetes Event Exporter</a> is able to watch, filter, and send Kubernetes events into the SkyWalking backend. SkyWalking then associates the events with the system metrics and displays an overview about when and how the metrics are affected by the events.</p>
<p>If you want to deploy SkyWalking Kubernetes Event Explorer with one line of commands, refer to <a class="" href="https://github.com/chaos-mesh/chaos-mesh-on-skywalking/blob/master/exporter-deployment.yaml" rel="noopener noreferrer" target="_blank">this document</a> to create configuration files in YAML format and then customize the parameters in the filters and exporters. Now, you can use the command <code>kubectl apply</code> to deploy SkyWalking Kubernetes Event Explorer.</p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="step-3-use-jmeter-to-increase-service-loads">Step 3: Use JMeter to increase service loads<a class="hash-link" href="https://chaos-mesh.org/blog/better-observability-for-chaos-engineering/#step-3-use-jmeter-to-increase-service-loads" title="Direct link to Step 3: Use JMeter to increase service loads">​</a></h2>
<p>To better observe the change in service performance, you need to increase the service loads on Spring Boot. In this tutorial, we use JMeter, a widely adopted Java testing tool, to increase the service loads.</p>
<p>Perform a stress test on <code>localhost:8079</code> using JMeter and add five threads to continuously increase the service loads.</p>
<p></p><figure style="margin: 0;"><img alt="JMeter Dashboard 1" class="img_hi9z" height="517" src="https://chaos-mesh.org/assets/images/jmeter-1-57604bd61820a513fba79f7e3fe622a5.png" width="1156" /><figcaption class="text--italic text--center">JMeter Dashboard 1</figcaption></figure><p></p>
<p></p><figure style="margin: 0;"><img alt="JMeter Dashboard 2" class="img_hi9z" height="429" src="https://chaos-mesh.org/assets/images/jmeter-2-5286dd8271fc4872d751d69f04c955a2.png" width="1525" /><figcaption class="text--italic text--center">JMeter Dashboard 2</figcaption></figure><p></p>
<p>Open the SkyWalking Dashboard. You can see that the access rate is 100%, and that the service loads reach about 5,300 calls per minute (CPM).</p>
<p></p><figure style="margin: 0;"><img alt="SkyWalking Dashboard" class="img_hi9z" height="934" src="https://chaos-mesh.org/assets/images/skywalking-dashboard-be15b01a2de79a2abddad3f33fc15346.png" width="1919" /><figcaption class="text--italic text--center">SkyWalking Dashboard</figcaption></figure><p></p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="step-4-inject-failures-via-chaos-mesh-and-observe-results">Step 4: Inject failures via Chaos Mesh and observe results<a class="hash-link" href="https://chaos-mesh.org/blog/better-observability-for-chaos-engineering/#step-4-inject-failures-via-chaos-mesh-and-observe-results" title="Direct link to Step 4: Inject failures via Chaos Mesh and observe results">​</a></h2>
<p>After you finish the three steps above, you can use the Chaos Dashboard to simulate stress scenarios and observe the change in service performance during chaos experiments.</p>
<p></p><figure style="margin: 0;"><img alt="StressChaos on Chaos Dashboard" class="img_hi9z" height="935" src="https://chaos-mesh.org/assets/images/chaos-dashboard-stresschaos-0958f21ef5a185aa16e9c2327a226fe0.png" width="1918" /><figcaption class="text--italic text--center">StressChaos on Chaos Dashboard</figcaption></figure><p></p>
<p>The following sections describe how service performance varies under the stress of three chaos conditions:</p>
<ul>
<li class="">
<p>CPU load: 10%; memory load: 128 MB</p>
<p>The first chaos experiment simulates low CPU usage. To display when a chaos experiment starts and ends, click the switching button on the right side of the dashboard. To learn whether the experiment is Applied to the system or Recovered from the system, move your cursor onto the short, green line.</p>
<p>During the time period between the two short, green lines, the service load decreases to 4,929 CPM, but returns to normal after the chaos experiment ends.</p>
<p></p><figure style="margin: 0;"><img alt="Test 1" class="img_hi9z" height="316" src="https://chaos-mesh.org/assets/images/cpuload-1-3188bd3a6afc8e73e4e8723b58518b20.png" width="722" /><figcaption class="text--italic text--center">Test 1</figcaption></figure><p></p>
</li>
<li class="">
<p>CPU load: 50%; memory load: 128 MB</p>
<p>When the application’s CPU load increases to 50%, the service load decreases to 4,307 CPM.</p>
<p></p><figure style="margin: 0;"><img alt="Test 2" class="img_hi9z" height="321" src="https://chaos-mesh.org/assets/images/cpuload-2-1ef91964d35ba5f9bceef75075756250.png" width="724" /><figcaption class="text--italic text--center">Test 2</figcaption></figure><p></p>
</li>
<li class="">
<p>CPU load: 100%; memory load: 128 MB</p>
<p>When the CPU usage is at 100%, the service load decreases to only 40% of what it would be if no chaos experiments were taking place.</p>
<p></p><figure style="margin: 0;"><img alt="Test 3" class="img_hi9z" height="321" src="https://chaos-mesh.org/assets/images/cpuload-3-8630b8200eca779f6f534a29ac08a65e.png" width="725" /><figcaption class="text--italic text--center">Test 3</figcaption></figure><p></p>
<p>Because the process scheduling under the Linux system does not allow a process to occupy the CPU all the time, the deployed Spring Boot Demo can still handle 40% of the access requests even in the extreme case of a full CPU load.</p>
</li>
</ul>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="summary">Summary<a class="hash-link" href="https://chaos-mesh.org/blog/better-observability-for-chaos-engineering/#summary" title="Direct link to Summary">​</a></h2>
<p>By combining SkyWalking and Chaos Mesh, you can clearly observe when and to what extent chaos experiments affect application service performance. This combination of tools lets you observe the service performance in various extreme conditions, thus boosting your confidence in your services.</p>
<p>Chaos Mesh has grown a lot in 2021 thanks to the unremitting efforts of all PingCAP engineers and community contributors. In order to continue to upgrade our support for our wide variety of users and learn more about users’ experience in Chaos Engineering, we’d like to invite you to take<a class="" href="https://www.surveymonkey.com/r/X77BCNM" rel="noopener noreferrer" target="_blank"> this survey</a> and give us your valuable feedback.</p>
<p>If you want to know more about Chaos Mesh, you’re welcome to join <a class="" href="https://github.com/chaos-mesh" rel="noopener noreferrer" target="_blank">the Chaos Mesh community on GitHub</a> or our <a class="" href="https://slack.cncf.io/" rel="noopener noreferrer" target="_blank">Slack discussions</a> (#project-chaos-mesh). If you find any bugs or missing features when using Chaos Mesh, you can submit your pull requests or issues to our <a class="" href="https://github.com/chaos-mesh/chaos-mesh" rel="noopener noreferrer" target="_blank">GitHub repository</a>.</p>
