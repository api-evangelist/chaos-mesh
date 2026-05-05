---
title: "Deploy Chaos Mesh on KubeSphere"
url: "https://chaos-mesh.org/blog/deploy-chaos-mesh-on-kubesphere/"
date: "Wed, 22 Dec 2021 00:00:00 GMT"
author: "cwenyin0@gmail.com (Cwen Yin)"
feed_url: "https://chaos-mesh.org/blog/rss.xml"
---
<p></p><figure style="margin: 0;"><img alt="Deploy Chaos Mesh on KubeSphere" class="img_hi9z" height="500" src="https://chaos-mesh.org/assets/images/chaos-mesh-kubesphere-banner-d1ac1761a1832e257e371d279ad9c82f.png" width="1500" /><figcaption class="text--italic text--center">Deploy Chaos Mesh on KubeSphere</figcaption></figure><p></p>
<p><a class="" href="https://github.com/chaos-mesh/chaos-mesh" rel="noopener noreferrer" target="_blank">Chaos Mesh</a> is a cloud-native Chaos Engineering platform that orchestrates chaos in Kubernetes environments. With Chaos Mesh, you can test your system's resilience and robustness on Kubernetes by injecting various types of faults into Pods, network, file system, and even the kernel.</p>
<!-- -->
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh architecture" class="img_hi9z" height="1398" src="https://chaos-mesh.org/assets/images/chaos-mesh-architecture-2.0-8f9608a528cf0eaab88b05032cc8a1f8.png" width="1999" /><figcaption class="text--italic text--center">Chaos Mesh architecture</figcaption></figure><p></p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="whats-kubesphere">What’s KubeSphere<a class="hash-link" href="https://chaos-mesh.org/blog/deploy-chaos-mesh-on-kubesphere/#whats-kubesphere" title="Direct link to What’s KubeSphere">​</a></h2>
<p><a class="" href="https://kubesphere.io/" rel="noopener noreferrer" target="_blank">KubeSphere</a> is a distributed operating system for cloud-native application management, using Kubernetes as its kernel. It provides a plug-and-play architecture, allowing third-party applications to be seamlessly integrated into its ecosystem.</p>
<p>KubeSphere 3.2.0 adds the feature of dynamically loading community-developed Helm charts into the <a class="" href="https://kubesphere.io/docs/pluggable-components/app-store/" rel="noopener noreferrer" target="_blank">KubeSphere App Store</a>. Thanks to this new feature, Chaos Mesh is now available on KubeSphere. In this tutorial, you will learn how to deploy Chaos Mesh on KubeSphere to conduct chaos experiments.</p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="enable-app-store-on-kubesphere">Enable App Store on KubeSphere<a class="hash-link" href="https://chaos-mesh.org/blog/deploy-chaos-mesh-on-kubesphere/#enable-app-store-on-kubesphere" title="Direct link to Enable App Store on KubeSphere">​</a></h2>
<ol>
<li class="">
<p>Make sure you have installed and enabled the <a class="" href="https://kubesphere.io/docs/pluggable-components/app-store/" rel="noopener noreferrer" target="_blank">KubeSphere App Store</a>.</p>
</li>
<li class="">
<p>You need to create a workspace, a project, and a user account (project-regular) for this tutorial. The account needs to be a platform regular user and to be invited as the project operator with the operator role. For more information, see <a class="" href="https://kubesphere.io/docs/quick-start/create-workspace-and-project/" rel="noopener noreferrer" target="_blank">Create Workspaces, Projects, Users and Roles</a>.</p>
</li>
</ol>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="chaos-experiments-with-chaos-mesh">Chaos experiments with Chaos Mesh<a class="hash-link" href="https://chaos-mesh.org/blog/deploy-chaos-mesh-on-kubesphere/#chaos-experiments-with-chaos-mesh" title="Direct link to Chaos experiments with Chaos Mesh">​</a></h2>
<h3 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="step-1-deploy-chaos-mesh">Step 1: Deploy Chaos Mesh<a class="hash-link" href="https://chaos-mesh.org/blog/deploy-chaos-mesh-on-kubesphere/#step-1-deploy-chaos-mesh" title="Direct link to Step 1: Deploy Chaos Mesh">​</a></h3>
<ol>
<li class="">
<p>Login KubeSphere as <code>project-regular</code>, search for <strong>chaos-mesh</strong> in the <strong>App Store</strong>, and click on the search result to enter the app.</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh app" class="img_hi9z" height="1132" src="https://chaos-mesh.org/assets/images/chaos-mesh-app-8adffd3053f397bb95fcda48a2c0a5a0.png" width="1999" /><figcaption class="text--italic text--center">Chaos Mesh app</figcaption></figure><p></p>
</li>
<li class="">
<p>In the <strong>App Information</strong> page, click <strong>Install</strong> on the upper right corner.</p>
<p></p><figure style="margin: 0;"><img alt="Install Chaos Mesh" class="img_hi9z" height="1090" src="https://chaos-mesh.org/assets/images/install-chaos-mesh-d521449e8a0d735b7a53389420471008.png" width="1999" /><figcaption class="text--italic text--center">Install Chaos Mesh</figcaption></figure><p></p>
</li>
<li class="">
<p>In the <strong>App Settings</strong> page, set the application <strong>Name,</strong> <strong>Location</strong> (as your Namespace), and <strong>App Version</strong>, and then click <strong>Next</strong> on the upper right corner.</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh basic information" class="img_hi9z" height="1245" src="https://chaos-mesh.org/assets/images/chaos-mesh-basic-info-08cf0a7bd5e76a47cbcc304eb25687ca.png" width="1999" /><figcaption class="text--italic text--center">Chaos Mesh basic information</figcaption></figure><p></p>
</li>
<li class="">
<p>Configure the <code>values.yaml</code> file as needed, or click <strong>Install</strong> to use the default configuration.</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh configurations" class="img_hi9z" height="1322" src="https://chaos-mesh.org/assets/images/chaos-mesh-config-09ac3ba9ad416620a5cdb4d6b63b36d2.png" width="1999" /><figcaption class="text--italic text--center">Chaos Mesh configurations</figcaption></figure><p></p>
</li>
<li class="">
<p>Wait for the deployment to be finished. Upon completion, Chaos Mesh will be shown as <strong>Running</strong> in KubeSphere.</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh deployed" class="img_hi9z" height="721" src="https://chaos-mesh.org/assets/images/chaos-mesh-deployed-363a24608b8daa7da207cbddf42604bf.png" width="1999" /><figcaption class="text--italic text--center">Chaos Mesh deployed</figcaption></figure><p></p>
</li>
</ol>
<h3 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="step-2-visit-chaos-dashboard">Step 2: Visit Chaos Dashboard<a class="hash-link" href="https://chaos-mesh.org/blog/deploy-chaos-mesh-on-kubesphere/#step-2-visit-chaos-dashboard" title="Direct link to Step 2: Visit Chaos Dashboard">​</a></h3>
<ol>
<li class="">
<p>In the <strong>Resource Status</strong> page, copy the **NodePort **of <code>chaos-dashboard</code>.</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh NodePort" class="img_hi9z" height="1183" src="https://chaos-mesh.org/assets/images/chaos-mesh-nodeport-a4d9f826906e930e860982726841b582.png" width="1999" /><figcaption class="text--italic text--center">Chaos Mesh NodePort</figcaption></figure><p></p>
</li>
<li class="">
<p>Access the Chaos Dashboard by entering <code>${NodeIP}:${NODEPORT}</code> in your browser. Refer to <a class="" href="https://chaos-mesh.org/docs/manage-user-permissions/" rel="noopener noreferrer" target="_blank">Manage User Permissions</a> to generate a Token and log into Chaos Dashboard.</p>
<p></p><figure style="margin: 0;"><img alt="Login to Chaos Dashboard" class="img_hi9z" height="767" src="https://chaos-mesh.org/assets/images/login-to-dashboard-a9c2d9c7daa5a4532e19add776db193d.png" width="1600" /><figcaption class="text--italic text--center">Login to Chaos Dashboard</figcaption></figure><p></p>
</li>
</ol>
<h3 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="step-3-create-a-chaos-experiment">Step 3: Create a chaos experiment<a class="hash-link" href="https://chaos-mesh.org/blog/deploy-chaos-mesh-on-kubesphere/#step-3-create-a-chaos-experiment" title="Direct link to Step 3: Create a chaos experiment">​</a></h3>
<p>Before creating a chaos experiment, you should identify and deploy your experiment target, for example, to test how an application works under network latency. Here, we use a demo application <code>web-show</code> as the target application to be tested, and the test goal is to observe the system network latency. You can deploy a demo application <code>web-show</code> with the following command: <code>web-show</code>.</p>
<div class="language-bash codeBlockContainer_pGZf theme-code-block"><div class="codeBlockContent_S_WQ"><pre class="prism-code language-bash codeBlock_Pb2F thin-scrollbar" style="color: #393A34; background-color: #f6f8fa;" tabindex="0"><code class="codeBlockLines_pJnY"><div class="token-line" style="color: #393A34;"><span class="token function" style="color: #d73a49;">curl</span><span class="token plain"> </span><span class="token parameter variable" style="color: #36acaa;">-sSL</span><span class="token plain"> https://mirrors.chaos-mesh.org/latest/web-show/deploy.sh </span><span class="token operator" style="color: #393A34;">|</span><span class="token plain"> </span><span class="token function" style="color: #d73a49;">bash</span><br /></div></code></pre></div></div>
<blockquote>
<p>Note: The network latency of the Pod can be observed directly from the web-show application pad to the kube-system pod.</p>
</blockquote>
<ol>
<li class="">
<p>From your web browser, visit <code>${NodeIP}:8081</code> to access the <strong>Web Show</strong> application.</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Mesh web show app" class="img_hi9z" height="748" src="https://chaos-mesh.org/assets/images/web-show-app-895d8add29dc5ead3186061140dd08c9.png" width="1600" /><figcaption class="text--italic text--center">Chaos Mesh web show app</figcaption></figure><p></p>
</li>
<li class="">
<p>Log in to Chaos Dashboard to create a chaos experiment. To observe the effect of network latency on the application, we set the **Target **as "Network Attack" to simulate a network delay scenario.</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Dashboard" class="img_hi9z" height="1263" src="https://chaos-mesh.org/assets/images/chaos-dashboard-networkchaos-b9db285317d00b05eb3bb07ebe582916.png" width="1999" /><figcaption class="text--italic text--center">Chaos Dashboard</figcaption></figure><p></p>
<p>The <strong>Scope</strong> of the experiment is set to <code>app: web-show</code>.</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Experiment scope" class="img_hi9z" height="1154" src="https://chaos-mesh.org/assets/images/chaos-experiment-scope-215b20d1a6b9e1e235ceca59079c01c1.png" width="1999" /><figcaption class="text--italic text--center">Chaos Experiment scope</figcaption></figure><p></p>
</li>
<li class="">
<p>Start the chaos experiment by submitting it.</p>
<p></p><figure style="margin: 0;"><img alt="Submit Chaos Experiment" class="img_hi9z" height="980" src="https://chaos-mesh.org/assets/images/start-chaos-experiment-d709c21f47e704f7349bf8627b4a2498.png" width="1999" /><figcaption class="text--italic text--center">Submit Chaos Experiment</figcaption></figure><p></p>
</li>
</ol>
<p>Now, you should be able to visit <strong>Web Show</strong> to observe experiment results:</p>
<p></p><figure style="margin: 0;"><img alt="Chaos Experiment result" class="img_hi9z" height="720" src="https://chaos-mesh.org/assets/images/experiment-result-fe46c56819b85b5e68bb0d3b27550424.png" width="1600" /><figcaption class="text--italic text--center">Chaos Experiment result</figcaption></figure><p></p>
<h2 class="anchor anchorTargetHideOnScrollNavbar_fkcC" id="to-summarize">To summarize<a class="hash-link" href="https://chaos-mesh.org/blog/deploy-chaos-mesh-on-kubesphere/#to-summarize" title="Direct link to To summarize">​</a></h2>
<p>KubeSphere makes cloud-native application deployments and maintenance easy. Thanks to the App Store, users can easily deploy Chaos Mesh on KubeSphere with just a few clicks, enabling you to quickly start your own chaos experiments.</p>
<p>To learn more about Chaos Mesh, refer to the <a class="" href="https://chaos-mesh.org/docs/" rel="noopener noreferrer" target="_blank">Chaos Mesh docs</a> or join the community Slack (<a class="" href="https://slack.cncf.io/" rel="noopener noreferrer" target="_blank">CNCF</a>/#project-chaos-mesh).</p>
