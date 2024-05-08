# JMESPath Playground

<script src="https://cdnjs.cloudflare.com/ajax/libs/jmespath/0.16.0/jmespath.min.js" integrity="sha512-w/sNKK/59oJUi6v+SjgfIijrkFN8Pfv5QFZSV4KvrNMJrlbVM3017ZGNCA2AwZ6PKJzTPxQaDs/TbPcVGnF+pQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.3/css/bootstrap.min.css" integrity="sha512-jnSuA4Ss2PkkikSOLtYs8BlYIeeIK1h99ty4YfvRPAlzr377vr3CXDb7sb7eEEBYjDtcYj+AjBH3FLv5uSJuXg==" crossorigin="anonymous" referrerpolicy="no-referrer" />

<div id="app" class="container border">
    <h3>Expression</h3>
    <input class="expression form-control" type="text" placeholder="Expression" value="a" />
    <h3>Data</h3>
    <textarea class="input form-control" rows="5" style="width:100%;">{"a": "foo", "b": "bar", "c": "hello-world"}</textarea>
    <h3>Result</h3>
    <pre class="result form-control" style="height:100%;"></pre>
</div>

<script>
    const app = document.getElementById('app');
    function evaluateDemo(el) {
        var expression = el.querySelector('.expression').value;
        var data = JSON.parse(el.querySelector('.input').value);
        var result = jmespath.search(data, expression);
        el.querySelector('.result').textContent = JSON.stringify(result, null, 2);
    }
    evaluateDemo(app);
    app.querySelector('.expression').addEventListener('input', () => evaluateDemo(app));
    app.querySelector('.input').addEventListener('input', () => evaluateDemo(app));
</script>
