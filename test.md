---


---

<h1 id="neweb-embed-payment---js-sdk">Neweb Embed payment - JS SDK</h1>
<h2 id="getting-started">Getting Started</h2>
<ol>
<li>This document is applicable to Newebpay’s normal embed pay with <strong>version 1.1</strong></li>
<li>Make sure you’re already  get ‘PassToken’. `</li>
</ol>
<h2 id="install-in-browser">Install in browser</h2>
<p>Include the script on needed page, it should always be loaded directly from <code>https://core.Newebpay.com</code>, rather than included in hosted yourself.</p>
<p><code>&lt;script src="https://core.NewebPay.com/js/normal_embed_pay_v1.1.js"&gt; &lt;/script&gt;</code></p>
<h2 id="usage">Usage</h2>
<p>Only the <code>passToken</code> is required option.</p>
<pre><code>&lt;script&gt;
    var nwpIframe = new NWPEbpay({
	    passToken: '', //set the 'passToken' you got through the API.
	    autoCreate: true,
	    content: 'nwpebp_js_content',
	    env: 'Prod',
	    width: '360px',
	    height: '240px'
	})
&lt;/script&gt;
</code></pre>
<h2 id="options">Options</h2>

<table>
<thead>
<tr>
<th>Name</th>
<th>Default (Is required)</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>passToken</td>
<td><code>null</code> (<strong>Required</strong>)</td>
<td>String</td>
<td>Please set the ‘passToken’ you got through the API.</td>
</tr>
<tr>
<td>autoCreate</td>
<td><code>true</code></td>
<td>Boolean</td>
<td>If didn’t want to display iframe immediately, please set to <code>false</code></td>
</tr>
<tr>
<td>content</td>
<td>nwpebp_js_content</td>
<td>String</td>
<td>Customize the <code>id</code> name of the <code>div</code> where you want to place the iframe.</td>
</tr>
<tr>
<td>env</td>
<td>Prod</td>
<td>String</td>
<td>Please set to <code>Test</code> when use testing environment.</td>
</tr>
<tr>
<td>width</td>
<td>360px</td>
<td>String</td>
<td>The width of iframe.</td>
</tr>
<tr>
<td>height</td>
<td>240px</td>
<td>String</td>
<td>The height of iframe.</td>
</tr>
</tbody>
</table><h2 id="methods">Methods</h2>
<h3 id="create">.create()</h3>
<p><code>nwpIframe.create()</code></p>
<p>If your options set <code>autoCreate</code> is <code>false</code>. When your page is ready to display iframe. You can use this methods be shown iframe.</p>
<h3 id="submit">.submit()</h3>
<p><code>nwpIframe.submit()</code></p>
<p>After entering the card number and other information, you can call this method to send the content</p>
<h2 id="fished">Fished</h2>
<p>After the transaction result is completed, the client will return the parameter in JSON format. Sent <code>TokenizedCard</code> to the backend for credit card authorization. Can use the following code to obtain the <code>TokenizedCard</code>.</p>
<pre><code>&lt;script&gt;
	window.addEventListener('message', function(e) {
		if(e.data.Status == 'SUCCESS') {
			TokenizedCard = e.data.Result.TokenizedCard; //get TokenizedCard
		} else {
			//error handle
			console.error(e);
		}
	})
&lt;/script&gt;
</code></pre>

