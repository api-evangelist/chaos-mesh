---
title: "Securing Online Gaming: Combine Chaos Engineering with DevOps Practices"
url: "https://chaos-mesh.org/blog/Securing-Online-Gaming-Combine-Chaos-Engineering-with-DevOps-Practices/"
date: "Thu, 26 Aug 2021 00:00:00 GMT"
author: ""
feed_url: "https://chaos-mesh.org/blog/rss.xml"
---
<p></p><figure style="margin: 0;"><img alt="Securing Online Gaming: Combine Chaos Engineering with DevOps Practices" class="img_hi9z" height="400" src="https://chaos-mesh.org/assets/images/chaos-mesh-tencent-ieg-3119a610ddb42163cb244e562167f680.jpeg" width="1200" /><figcaption class="text--italic text--center">Securing Online Gaming: Combine Chaos Engineering with DevOps Practices</figcaption></figure><p></p>
<p>Interactive Entertainment Group (IEG) is a division of Tencent Holdings that focuses on the development of online video games and other digital content such as live broadcasts. It is well-known for being the publisher of some of the most popular video games.</p>
<!-- -->
<p>In this article, I will explain why and how we introduce chaos engineering into our DevOps process.</p>
<p>For each day, we handle over 10,000,000 total visits, and, during peak hours, we process over 1,000,000 queries per second (QPS). To guarantee players a fun and engaging experience, we launch various daily or seasonal game events. Sometimes, that means we must update the event code over 500 times per day. As our user base grows, the total amount of data quickly multiplies. Currently, the figure stands at 200 terabytes. We have to manage the massive user queries and rapid release iterations, and we managed it well.</p>
<p>A cloud-native DevOps solution frees our events operator from the growing number of online events. We developed a pipeline that takes care of everything they need, from writing code to launching events in production environments: once new event codes are detected, the operation platform automatically builds images from them and deploys the image to Tencent Kubernetes Engine (TKE). You might be wondering how long this entire automated process takes: only 5 minutes.</p>
<p>Currently, almost all IEG operation services run in TKE. Elastic scaling promises faster capacity expansion and reduction of cloud services thanks to cloud-native technology.</p>
<p>In addition, we expect the iterations to be easier. A best practice is to break down the large, hard-to-maintain service into many “smaller” services that we can maintain independently. “Small” services have less code and simpler logic, with lower handover and training costs. We as developers continue to practice this kind of microservices architecture as part of DevOps initiatives. Yet similar issues persist. As the number of services increases, so does the complexity of making calls between them. <strong>Worse, if one “small” service fails, it could set off a chain reaction that brings all the services down—a microservice dependency hell.</strong></p>
<p>The thing is, fault tolerance varies by service. Some support downgrading, while others don’t. Not to mention that some services are unable to provide timely alerts or lack an effective debugging tool. As a result, debugging services has become a tricky and increasingly pressing issue in our day-to-day work.</p>
<p>But we can’t just let it be. What if the unstable performance constantly chases our players away? What if there is a catastrophic failure?</p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="let-there-be-faults">Let there be faults<a class="hash-link" href="https://chaos-mesh.org/blog/Securing-Online-Gaming-Combine-Chaos-Engineering-with-DevOps-Practices/#let-there-be-faults" title="Direct link to Let there be faults">​</a></h2>
<p>Netflix introduced the idea of chaos engineering. This approach tests the resilience of the system against all kinds of edgy cases by injecting faults in a non-production environment to achieve ideal system reliability. According to one Gartner article, by 2023, 40% of organizations will use chaos engineering to meet their top DevOps objectives, reducing unplanned downtime by 20%.</p>
<p>This is exactly how we avoid the worst-case scenario. Fault injection, in my opinion, is now a must-do in every technical team. In our early test cases, developers would bring down a node before launching a service to see if the primary node automatically switched to the secondary node and if disaster recovery worked.</p>
<p><strong>But chaos engineering is more than fault injection.</strong> It is a field that constantly drives new techniques, professional testing tools, and solid theories. That’s why we continue to explore it.</p>
<p>IEG officially launched its chaos engineering project over a year ago. We wanted to do this right the first time. The key is to select a chaos engineering tool that supports running experiments in the Kubernetes environment. <strong>After a careful comparison, we believe <a class="" href="https://github.com/chaos-mesh/chaos-mesh" rel="noopener noreferrer" target="_blank">Chaos Mesh</a> is our best option</strong> because:</p>
<ul>
<li class="">It is a Cloud Native Computing Foundation (CNCF) Sandbox project with a friendly and productive community.</li>
<li class="">It does not intrude on existing applications.</li>
<li class="">It provides a web UI and a variety of fault injection types, as shown in the image below.</li>
</ul>
<p></p><figure style="margin: 0;"><img alt="A comparison of chaos engineering tools" class="img_hi9z" height="712" src="https://chaos-mesh.org/assets/images/comparison-of-chaos-engineering-tools-7dba9d470020b2a7250e50e1413aec74.png" width="1080" /><figcaption class="text--italic text--center">A comparison of chaos engineering tools</figcaption></figure><p></p>
<blockquote>
<p>Note: This comparison is outdated and is intended simply to compare fault injection features supported by Chaos Mesh with other well-known chaos engineering platforms. It is not intended to favor or position one project over another. Any corrections are welcome.</p>
</blockquote>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="build-a-chaos-testing-platform">Build a chaos testing platform<a class="hash-link" href="https://chaos-mesh.org/blog/Securing-Online-Gaming-Combine-Chaos-Engineering-with-DevOps-Practices/#build-a-chaos-testing-platform" title="Direct link to Build a chaos testing platform">​</a></h2>
<p>Our chaos engineering team embedded Chaos Mesh into our continuous integration and continuous delivery pipelines. As shown in the diagram below, Chaos Mesh now plays an important role in our operation platform. We use Chaos Mesh's dashboard API to create, run, and delete chaos experiments and monitor them on our own platform. We can simulate basic system-level faults in Pods, container, network, and IO.</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh embedded in IEG&amp;#39;s operation platform" class="img_hi9z" height="915" src="https://chaos-mesh.org/assets/images/chaos-mesh-embedded-in-IEG's-operation-platform-afaf1b549e9a7d2b6103a16dfb6eb4c6.png" width="1999" /><figcaption class="text--italic text--center">Chaos Mesh embedded in IEG's operation platform</figcaption></figure><p></p>
<p>In IEG, <strong>chaos engineering is generally summarized as a closed loop with several key phases</strong>:</p>
<ul>
<li class="">
<p>Improve overall system resilience.</p>
<p>Build a chaos testing platform that we can modify as our needs change.</p>
</li>
<li class="">
<p>Design a testing plan.</p>
<p>The testing plan must specify the target, scope, fault to be injected, monitoring metrics, etc. Make sure the testing is well-controlled.</p>
</li>
<li class="">
<p>Execute chaos experiments and review the results.</p>
<p>Compare the system’s performance before and after the chaos experiment.</p>
</li>
<li class="">
<p>Resolve any issues that may arise.</p>
<p>Fix found issues and upgrade the system for the follow-up experiment.</p>
</li>
<li class="">
<p>Repeat chaos experiments and verify performance.</p>
<p>Repeat chaos experiments to see if the system’s performance meets expectations. If it does, design another testing plan.</p>
</li>
</ul>
<p></p><figure style="margin: 0;"><img alt="Five phases of chaos engineering in IEG" class="img_hi9z" height="1721" src="https://chaos-mesh.org/assets/images/five-phases-of-chaos-engineering-in-IEG-ecfa298a68587aa59ba778bb563e30fd.png" width="1999" /><figcaption class="text--italic text--center">Five phases of chaos engineering in IEG</figcaption></figure><p></p>
<p>We frequently <strong>test the performance of services under high CPU usage</strong>, for example. We begin by orchestrating and scheduling experiments. Following that, we run experiments and monitor the performance of related services. Multiple monitoring metrics, such as QPS, latency, response success, are immediately visible through the operation platform. The platform then generates reports for us to review, so we can check whether these experiments met our expectations.</p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="use-cases">Use cases<a class="hash-link" href="https://chaos-mesh.org/blog/Securing-Online-Gaming-Combine-Chaos-Engineering-with-DevOps-Practices/#use-cases" title="Direct link to Use cases">​</a></h2>
<p>The following are a few examples of how we use chaos engineering in our DevOps workflow.</p>
<h3 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="finer-granularity-of-fault-injection">Finer granularity of fault injection<a class="hash-link" href="https://chaos-mesh.org/blog/Securing-Online-Gaming-Combine-Chaos-Engineering-with-DevOps-Practices/#finer-granularity-of-fault-injection" title="Direct link to Finer granularity of fault injection">​</a></h3>
<p>There is no need to shut down the entire system to see if our games are still available to players. Sometimes we only want to inject faults, say, network latency, into a single game account, and observe how it responds. We are now able to achieve this finer granularity by hijacking traffic and running experiments at the gateway.</p>
<h3 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="red-teaming">Red teaming<a class="hash-link" href="https://chaos-mesh.org/blog/Securing-Online-Gaming-Combine-Chaos-Engineering-with-DevOps-Practices/#red-teaming" title="Direct link to Red teaming">​</a></h3>
<p>Understandably, our team members grew bored of regular chaos experiments. After all, it’s something like telling your left hand to fight against your right hand. Here at IEG, <strong>we integrate a testing practice called red teaming into chaos engineering to ensure that our system resiliency improves in an organic way.</strong> Red teaming is similar to penetration testing, but more targeted. It requires a group of testers to emulate real-world attacks from an outsider’s perspective. If I were in charge of IT operations, I would simulate faults to specific services, and check to see whether my developer colleges were doing a good job. If I found any potential faults, well, be prepared for some “hard talk.” On the other hand, developers would actively perform chaos experiments and make sure no risk was left behind to avoid being blamed.</p>
<p></p><figure style="margin: 0;"><img alt="The red teaming process in IEG" class="img_hi9z" height="1957" src="https://chaos-mesh.org/assets/images/red-teaming-process-in-IEG-9c4e15b2baa0791bb078de705ec915fe.png" width="1999" /><figcaption class="text--italic text--center">The red teaming process in IEG</figcaption></figure><p></p>
<h3 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="dependency-analysis">Dependency analysis<a class="hash-link" href="https://chaos-mesh.org/blog/Securing-Online-Gaming-Combine-Chaos-Engineering-with-DevOps-Practices/#dependency-analysis" title="Direct link to Dependency analysis">​</a></h3>
<p>It’s important to manage dependencies for microservices. In our case, non-core services cannot be the bottleneck for core services. Fortunately, with chaos engineering, we can run dependency analysis simply by injecting faults into called services and observing how badly the main service is affected. Based on the results, we can optimize the service calling chain in a specific scenario.</p>
<h3 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="automated-fault-detection-and-diagnosis">Automated fault detection and diagnosis<a class="hash-link" href="https://chaos-mesh.org/blog/Securing-Online-Gaming-Combine-Chaos-Engineering-with-DevOps-Practices/#automated-fault-detection-and-diagnosis" title="Direct link to Automated fault detection and diagnosis">​</a></h3>
<p>We are also exploring AI bots to help us detect and diagnose faults. As services become more complex, the likelihood of failure increases. <strong>Our goal is to train a fault detection model through large-scale chaos experiments in production or other controlled environments.</strong></p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="chaos-engineering-empowers-devops-practices">Chaos engineering empowers DevOps practices<a class="hash-link" href="https://chaos-mesh.org/blog/Securing-Online-Gaming-Combine-Chaos-Engineering-with-DevOps-Practices/#chaos-engineering-empowers-devops-practices" title="Direct link to Chaos engineering empowers DevOps practices">​</a></h2>
<p>Currently, on average, more than 50 people run chaos experiments each week, running more than 150 tests, and detecting more than 100 problems in total.</p>
<p>Gone are the days when performing fault injection requires a handwritten script, which can be a tough thing to do for those who are unfamiliar with it. <strong>The benefits of combining chaos engineering with DevOps practices are obvious: within a few minutes, you can orchestrate various fault types by simply dragging and dropping, execute them with a single click, and monitor the results in real-time—all in one platform.</strong></p>
<p></p><figure style="margin: 0;"><img alt="Chaos engineering with DevOps ensures efficient fault injection" class="img_hi9z" height="568" src="https://chaos-mesh.org/assets/images/chaos-engineering-with-devops-5f6fab8a9cb2ab88dd0915d536f5de6f.png" width="1999" /><figcaption class="text--italic text--center">Chaos engineering with DevOps ensures efficient fault injection</figcaption></figure><p></p>
<p>Thanks to full-featured chaos engineering tools and streamlined DevOps processes, we estimate that the efficiency of fault injection and chaos-based optimization at IEG has been improved at least by 10 times in the last six months. If you were unsure about implementing chaos engineering in your business, I hope our experience can be of some help.</p>
