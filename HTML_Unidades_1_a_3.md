# HTML del curso Diseño Instruccional con Inteligencia Artificial

Compilación de los archivos HTML desarrollados para las Unidades 1 a 3.

## Índice

### Unidad 1
- `AF1-1-delegar.html`
- `AF1-2-prompts.html`
- `AF1-3-brief.html`
- `CI1-3-brief.html`
- `CI1-3-certeza.html`
- `CI2-1-escalas-diseno.html`
- `CI2-1-bonus-resultado.html`
- `CI2-1-auditar-criterios.html`
- `AF2-1-evidencia-auditoria.html`

### Unidad 2
- `CI2-2-prompt-vs-asistente.html`
- `CI2-2-configurar-asistente.html`
- `CI3-2-hecho-interpretacion.html`

### Unidad 3


# Unidad 1

## AF1-1-delegar.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>¿Qué delegaría a la IA?</title>

<style>

:root{
  --teal:#17A9B8;
  --teal-dark:#087D8D;
  --teal-soft:#EAF8F8;
  --ink:#0B2B3D;
  --muted:#58737C;
  --line:#CFE5E7;
  --ok:#1F8F68;
  --ok-bg:#EFFAF5;
  --bad:#CC514B;
  --bad-bg:#FFF3F1;
}

*{
  box-sizing:border-box;
}

body{
  margin:0;
  padding:8px;
  background:#F4FAFB;
  font-family:Poppins,Arial,Helvetica,sans-serif;
  color:var(--ink);
}

.activity{
  max-width:1000px;
  margin:0 auto;
  background:#FFFFFF;
  border:1px solid #D6EEF2;
  border-radius:14px;
  overflow:hidden;
}


/* PANTALLAS */

.screen{
  display:none;
}

.screen.active{
  display:block;
}


/* PORTADA */

.cover{
  padding:44px 40px 46px;
  text-align:center;
}

.cover-icon{
  width:62px;
  height:62px;
  border-radius:50%;
  margin:0 auto 20px;
  background:#00B3C7;
  color:#FFFFFF;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:30px;
  font-weight:700;
}

.cover h1{
  margin:0 0 8px;
  font-size:27px;
  line-height:1.25;
  color:#0B2B3D;
}

.cover h2{
  margin:0 auto 20px;
  max-width:700px;
  font-size:21px;
  line-height:1.4;
  font-weight:500;
  color:#078A9A;
}

.cover p{
  max-width:760px;
  margin:0 auto 22px;
  font-size:16px;
  line-height:1.6;
  color:#526B76;
}

.cover-topics{
  max-width:720px;
  margin:0 auto 26px;
  padding:13px 20px;
  background:#F4FAFB;
  border:1px solid #D6EEF2;
  border-radius:10px;
  font-size:16px;
  font-weight:600;
  color:#0B2B3D;
}


/* PROGRESO */

.progress{
  display:none;
  justify-content:center;
  align-items:center;
  gap:7px;
  padding:10px 16px;
  background:#F8FCFD;
  border-bottom:1px solid #DCE6E9;
}

.progress.show{
  display:flex;
}

.step{
  width:26px;
  height:26px;
  border-radius:50%;
  border:1.5px solid #B9DBE1;
  background:#FFFFFF;
  color:#6B8791;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:12px;
  font-weight:600;
}

.step.active{
  background:#00B3C7;
  border-color:#00B3C7;
  color:#FFFFFF;
}

.step.done{
  background:#2D8692;
  border-color:#2D8692;
  color:#FFFFFF;
}

.line{
  width:42px;
  height:1.5px;
  background:#CBE5E9;
}


/* CONTENIDO */

.content{
  display:none;
  padding:24px 40px 32px;
}

.kicker{
  margin:0 0 12px;
  text-align:center;
  color:#078A9A;
  text-transform:uppercase;
  letter-spacing:.7px;
  font-size:13px;
  font-weight:700;
}

.context{
  max-width:820px;
  margin:0 auto 20px;
  padding:16px 18px;
  background:#F4FAFB;
  border-left:4px solid #2D8692;
  border-radius:0 10px 10px 0;
  font-size:16px;
  line-height:1.55;
  color:#314753;
}

.question{
  max-width:850px;
  margin:0 auto 22px;
  text-align:center;
  font-size:20px;
  line-height:1.45;
  font-weight:600;
}


/* OPCIONES */

.options{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:12px;
  max-width:860px;
  margin:0 auto;
}

.option{
  min-height:105px;
  border:1.5px solid #C6DCE1;
  border-radius:12px;
  background:#FFFFFF;
  padding:18px 14px;
  cursor:pointer;
  text-align:center;
  font-family:inherit;
  font-size:16px;
  font-weight:700;
  line-height:1.35;
  color:#0B2B3D;
  transition:.15s ease;
}

.option:hover:not(:disabled),
.option:focus:not(:disabled){
  background:#F8FCFD;
  border-color:#00B3C7;
}

.option:disabled{
  cursor:default;
}

.mini{
  width:30px;
  height:30px;
  border-radius:8px;
  display:flex;
  align-items:center;
  justify-content:center;
  background:#E9F8F8;
  border:1px solid #C5E6E8;
  margin:0 auto 11px;
  color:#0D92A2;
  font-size:14px;
}

.option.correct{
  border:2px solid var(--ok);
  background:var(--ok-bg);
}

.option.wrong{
  border:2px solid #E56E65;
  background:var(--bad-bg);
}


/* RETROALIMENTACIÓN */

.feedback{
  display:none;
  max-width:860px;
  margin:18px auto 0;
  border-radius:10px;
  padding:15px 17px;
  font-size:15px;
  line-height:1.5;
}

.feedback.show{
  display:block;
}

.feedback.ok{
  background:#F0FAF5;
  border:1px solid #B7DFC9;
  color:#17633F;
}

.feedback.bad{
  background:#FFF3F3;
  border:1px solid #F1BBBB;
  color:#932F2F;
}

.feedback strong{
  display:block;
  margin-bottom:4px;
}


/* BOTONES */

.actions{
  display:none;
  max-width:860px;
  margin:16px auto 0;
  justify-content:flex-end;
}

.actions.show{
  display:flex;
}

.btn{
  border:0;
  border-radius:9px;
  background:#00A6B8;
  color:#FFFFFF;
  padding:11px 20px;
  font-family:inherit;
  font-size:15px;
  font-weight:700;
  cursor:pointer;
}

.btn:hover,
.btn:focus{
  background:#078A9A;
}

.btn.secondary{
  background:#EAF8F8;
  color:#087D8D;
  border:1px solid #B7E4E6;
}


/* FINAL */

.finish{
  text-align:center;
  padding:30px 20px;
}

.finish-icon{
  width:58px;
  height:58px;
  border-radius:50%;
  margin:0 auto 16px;
  background:#00B3C7;
  color:#FFFFFF;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:28px;
  font-weight:700;
}

.finish h2{
  margin:0 0 10px;
  font-size:24px;
}

.finish p{
  max-width:680px;
  margin:0 auto 22px;
  font-size:16px;
  line-height:1.55;
  color:#526B76;
}


/* RESPONSIVE */

@media(max-width:700px){

  body{
    padding:4px;
  }

  .cover{
    padding:32px 20px 34px;
  }

  .cover h1{
    font-size:24px;
  }

  .cover h2{
    font-size:19px;
  }

  .content{
    padding:20px 16px 26px;
  }

  .question{
    font-size:18px;
  }

  .options{
    grid-template-columns:1fr;
  }

  .option{
    min-height:auto;
  }

  .line{
    width:24px;
  }

}

</style>
</head>


<body>

<div class="activity">


<!-- PORTADA -->

<div class="screen active" id="cover">

  <div class="cover">

    <div class="cover-icon">?</div>

    <h1>
      La IA puede hacerlo...
    </h1>

    <h2>
      ¿pero qué papel debería tener?
    </h2>

    <p>
      Lea cada situación y seleccione el nivel de participación que considere más adecuado.
      Si su elección no es correcta, revise la retroalimentación e inténtelo nuevamente.
      <strong>Avanzará cuando encuentre la respuesta adecuada.</strong>
    </p>

    <div class="cover-topics">
      IA puede apoyar
      &nbsp;&middot;&nbsp;
      IA + supervisión
      &nbsp;&middot;&nbsp;
      Decisión profesional
    </div>

    <button class="btn" onclick="startActivity()">
      Comenzar →
    </button>

  </div>

</div>


<!-- PROGRESO -->

<div class="progress" id="progress">

  <div class="step active" id="step1">1</div>
  <div class="line"></div>

  <div class="step" id="step2">2</div>
  <div class="line"></div>

  <div class="step" id="step3">3</div>
  <div class="line"></div>

  <div class="step" id="step4">4</div>

</div>


<div class="content" id="content">


<!-- PREGUNTA 1 -->

<div class="screen active" id="q1">

  <p class="kicker">
    Pregunta 1
  </p>

  <div class="question">
    Necesita resumir cinco documentos que usted mismo proporciona a la herramienta.
  </div>

  <div class="options">

    <button class="option" onclick="answer(1,'A',this)">
      <div class="mini">A</div>
      IA puede apoyar
    </button>

    <button class="option" onclick="answer(1,'B',this)">
      <div class="mini">B</div>
      Decisión profesional
    </button>

    <button class="option" onclick="answer(1,'C',this)">
      <div class="mini">C</div>
      IA + supervisión
    </button>

  </div>

  <div class="feedback" id="feedback1"></div>
  <div class="actions" id="actions1"></div>

</div>


<!-- PREGUNTA 2 -->

<div class="screen" id="q2">

  <p class="kicker">
    Pregunta 2
  </p>

  <div class="context">
    Dispone de registros de participación, resultados de evaluación y comentarios
    de estudiantes de un curso con alta deserción.
  </div>

  <div class="question">
    Desea utilizar IA para identificar posibles factores asociados al abandono.
    ¿Qué nivel de participación sería más adecuado?
  </div>

  <div class="options">

    <button class="option" onclick="answer(2,'A',this)">
      <div class="mini">A</div>
      Decisión profesional
    </button>

    <button class="option" onclick="answer(2,'B',this)">
      <div class="mini">B</div>
      IA + supervisión
    </button>

    <button class="option" onclick="answer(2,'C',this)">
      <div class="mini">C</div>
      IA puede apoyar
    </button>

  </div>

  <div class="feedback" id="feedback2"></div>
  <div class="actions" id="actions2"></div>

</div>


<!-- PREGUNTA 3 -->

<div class="screen" id="q3">

  <p class="kicker">
    Pregunta 3
  </p>

  <div class="context">
    Necesita diseñar un curso nuevo, pero todavía no dispone de información
    sobre los conocimientos, necesidades o características de los participantes.
  </div>

  <div class="question">
    ¿Qué papel debería tener la IA si se plantea construir el perfil de los participantes?
  </div>

  <div class="options">

    <button class="option" onclick="answer(3,'A',this)">
      <div class="mini">A</div>
      IA + supervisión
    </button>

    <button class="option" onclick="answer(3,'B',this)">
      <div class="mini">B</div>
      IA puede apoyar
    </button>

    <button class="option" onclick="answer(3,'C',this)">
      <div class="mini">C</div>
      Decisión profesional
    </button>

  </div>

  <div class="feedback" id="feedback3"></div>
  <div class="actions" id="actions3"></div>

</div>


<!-- PREGUNTA 4 -->

<div class="screen" id="q4">

  <p class="kicker">
    Pregunta 4
  </p>

  <div class="context">
    Proporciona a una IA información sobre la necesidad, los participantes,
    el contexto y el resultado esperado.
  </div>

  <div class="question">
    Le solicita una propuesta inicial de actividades y evaluación para una unidad.
    ¿Qué nivel de participación sería más adecuado?
  </div>

  <div class="options">

    <button class="option" onclick="answer(4,'A',this)">
      <div class="mini">A</div>
      IA + supervisión
    </button>

    <button class="option" onclick="answer(4,'B',this)">
      <div class="mini">B</div>
      Decisión profesional
    </button>

    <button class="option" onclick="answer(4,'C',this)">
      <div class="mini">C</div>
      IA puede apoyar
    </button>

  </div>

  <div class="feedback" id="feedback4"></div>
  <div class="actions" id="actions4"></div>

</div>


<!-- FINAL -->

<div class="screen" id="finish">

  <div class="finish">

    <div class="finish-icon">✓</div>

    <h2>
      Actividad completada
    </h2>

    <p>
      La IA puede apoyar tareas, ampliar posibilidades y colaborar en el análisis.
      A medida que aumenta la interpretación, el impacto o la responsabilidad de una decisión,
      también debe aumentar la intervención profesional.
    </p>

    <button class="btn secondary" onclick="restartActivity()">
      Volver a realizar
    </button>

  </div>

</div>


</div>
</div>


<script>


const correctAnswers = {
  1:"A",
  2:"B",
  3:"C",
  4:"A"
};


const correctFeedback = {

  1:
  "La IA puede agilizar la síntesis porque trabaja con información disponible y el resultado puede contrastarse directamente con los documentos originales.",

  2:
  "La IA puede identificar patrones y relaciones iniciales, pero interpretar esos patrones requiere revisar los datos, el contexto y otras explicaciones posibles.",

  3:
  "La información que todavía no existe debe investigarse o recopilarse. La IA no debería convertir supuestos sobre los participantes en datos del proyecto.",

  4:
  "La IA puede generar una propuesta inicial, pero la alineación, pertinencia y factibilidad deben revisarse antes de incorporarla al diseño."

};


const wrongFeedback = {

  1:
  "En este caso existe información concreta y el resultado es fácil de verificar. La IA puede utilizarse como apoyo para agilizar la síntesis.",

  2:
  "Aquí la IA no solo organiza información: también ayuda a interpretar posibles relaciones. Por eso el resultado necesita supervisión profesional.",

  3:
  "Si no existe evidencia sobre los participantes, una descripción generada por IA sería una inferencia y no un diagnóstico del proyecto.",

  4:
  "La propuesta afecta decisiones pedagógicas importantes. La IA puede aportar alternativas, pero el resultado necesita revisión profesional."

};


function startActivity(){

  document
    .getElementById("cover")
    .classList.remove("active");

  document
    .getElementById("progress")
    .classList.add("show");

  document
    .getElementById("content")
    .style.display="block";

  document
    .getElementById("q1")
    .classList.add("active");

  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}


function answer(questionNumber,selected,button){

  const screen =
    document.getElementById("q"+questionNumber);

  const options =
    screen.querySelectorAll(".option");

  const feedback =
    document.getElementById("feedback"+questionNumber);

  const actions =
    document.getElementById("actions"+questionNumber);


  options.forEach(function(option){
    option.disabled=true;
  });


  feedback.className="feedback show";
  actions.className="actions show";


  if(selected===correctAnswers[questionNumber]){

    button.classList.add("correct");

    feedback.classList.add("ok");

    feedback.innerHTML=
      "<strong>Decisión acertada</strong>"+
      correctFeedback[questionNumber];

    actions.innerHTML=
      '<button class="btn" onclick="nextQuestion('+
      questionNumber+
      ')">Continuar →</button>';

  }

  else{

    button.classList.add("wrong");

    feedback.classList.add("bad");

    feedback.innerHTML=
      "<strong>Revise su decisión</strong>"+
      wrongFeedback[questionNumber];

    actions.innerHTML=
      '<button class="btn" onclick="retryQuestion('+
      questionNumber+
      ')">Intentar de nuevo</button>';

  }

}


function retryQuestion(questionNumber){

  const screen =
    document.getElementById("q"+questionNumber);

  screen
    .querySelectorAll(".option")
    .forEach(function(option){

      option.disabled=false;
      option.classList.remove("correct","wrong");

    });


  const feedback =
    document.getElementById("feedback"+questionNumber);

  const actions =
    document.getElementById("actions"+questionNumber);


  feedback.className="feedback";
  feedback.innerHTML="";

  actions.className="actions";
  actions.innerHTML="";

}


function nextQuestion(current){

  document
    .getElementById("q"+current)
    .classList.remove("active");


  const currentStep =
    document.getElementById("step"+current);

  if(currentStep){

    currentStep.classList.remove("active");
    currentStep.classList.add("done");

  }


  if(current<4){

    const next=current+1;

    document
      .getElementById("q"+next)
      .classList.add("active");

    document
      .getElementById("step"+next)
      .classList.add("active");

  }

  else{

    document
      .getElementById("progress")
      .classList.remove("show");

    document
      .getElementById("finish")
      .classList.add("active");

  }


  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}


function restartActivity(){

  document
    .querySelectorAll(".screen")
    .forEach(function(screen){
      screen.classList.remove("active");
    });


  document
    .getElementById("cover")
    .classList.add("active");


  document
    .getElementById("progress")
    .classList.remove("show");


  document
    .getElementById("content")
    .style.display="none";


  document
    .querySelectorAll(".step")
    .forEach(function(step){

      step.classList.remove("active","done");

    });


  document
    .getElementById("step1")
    .classList.add("active");


  for(let q=1;q<=4;q++){

    const screen=
      document.getElementById("q"+q);


    screen
      .querySelectorAll(".option")
      .forEach(function(option){

        option.disabled=false;
        option.classList.remove("correct","wrong");

      });


    document
      .getElementById("feedback"+q)
      .className="feedback";

    document
      .getElementById("feedback"+q)
      .innerHTML="";


    document
      .getElementById("actions"+q)
      .className="actions";

    document
      .getElementById("actions"+q)
      .innerHTML="";

  }


  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}


</script>

</body>
</html>

```

## AF1-2-prompts.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Actividad Formativa 2</title>

<style>

*{
  box-sizing:border-box;
}

body{
  margin:0;
  padding:8px;
  background:#F4FAFB;
  font-family:Poppins, Arial, sans-serif;
  color:#0B2B3D;
}

.activity{
  max-width:1000px;
  margin:0 auto;
  background:#ffffff;
  border:1px solid #D6EEF2;
  border-radius:14px;
  overflow:hidden;
}

/* PANTALLAS */

.screen{
  display:none;
}

.screen.active{
  display:block;
}

/* PORTADA */

.cover{
  padding:44px 40px 46px;
  text-align:center;
}

.cover-icon{
  width:62px;
  height:62px;
  border-radius:50%;
  margin:0 auto 20px;
  background:#00B3C7;
  color:#ffffff;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:30px;
  font-weight:700;
}

.cover h1{
  margin:0 0 8px;
  font-size:27px;
  line-height:1.25;
  color:#0B2B3D;
}

.cover h2{
  margin:0 auto 20px;
  max-width:700px;
  font-size:21px;
  line-height:1.4;
  font-weight:500;
  color:#078A9A;
}

.cover p{
  max-width:760px;
  margin:0 auto 22px;
  font-size:16px;
  line-height:1.6;
  color:#526B76;
}

.cover-topics{
  max-width:680px;
  margin:0 auto 26px;
  padding:13px 20px;
  background:#F4FAFB;
  border:1px solid #D6EEF2;
  border-radius:10px;
  font-size:16px;
  font-weight:600;
  color:#0B2B3D;
}

/* PROGRESO */

.progress{
  display:none;
  justify-content:center;
  align-items:center;
  gap:7px;
  padding:10px 16px;
  background:#F8FCFD;
  border-bottom:1px solid #DCE6E9;
}

.progress.show{
  display:flex;
}

.step{
  width:26px;
  height:26px;
  border-radius:50%;
  border:1.5px solid #B9DBE1;
  background:#ffffff;
  color:#6B8791;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:12px;
  font-weight:600;
}

.step.active{
  background:#00B3C7;
  border-color:#00B3C7;
  color:#ffffff;
}

.step.done{
  background:#2D8692;
  border-color:#2D8692;
  color:#ffffff;
}

.line{
  width:42px;
  height:1.5px;
  background:#CBE5E9;
}

/* CONTENIDO */

.content{
  padding:24px 40px 32px;
}

.kicker{
  margin:0 0 8px;
  color:#078A9A;
  text-transform:uppercase;
  letter-spacing:.7px;
  font-size:13px;
  font-weight:700;
}

.question{
  margin:0 0 20px;
  font-size:20px;
  line-height:1.45;
  font-weight:600;
}

.question.small{
  font-size:18px;
}

.context{
  margin:0 0 20px;
  padding:16px 18px;
  background:#F4FAFB;
  border-left:4px solid #2D8692;
  border-radius:0 10px 10px 0;
  font-size:16px;
  line-height:1.55;
  color:#314753;
}

.options{
  display:grid;
  gap:11px;
}

.option{
  width:100%;
  border:1.5px solid #C6DCE1;
  border-radius:11px;
  background:#ffffff;
  padding:15px 17px;
  text-align:left;
  font-family:inherit;
  font-size:16px;
  line-height:1.4;
  color:#0B2B3D;
  cursor:pointer;
  transition:.15s ease;
}

.option:hover{
  border-color:#00B3C7;
  background:#F8FCFD;
}

.option strong{
  color:#078A9A;
  margin-right:8px;
}

.option.wrong{
  border:2px solid #E54B4B;
  background:#FFF5F5;
}

.option.correct{
  border:2px solid #2A9D71;
  background:#F1FBF6;
}

.option:disabled{
  cursor:default;
}

/* FEEDBACK */

.feedback{
  display:none;
  margin-top:20px;
  padding:15px 17px;
  border-radius:10px;
  font-size:15px;
  line-height:1.5;
}

.feedback.show{
  display:block;
}

.feedback.wrong{
  background:#FFF3F3;
  border:1px solid #F1BBBB;
  color:#932F2F;
}

.feedback.correct{
  background:#F0FAF5;
  border:1px solid #B7DFC9;
  color:#17633F;
}

.actions{
  display:none;
  margin-top:16px;
}

.actions.show{
  display:flex;
  justify-content:flex-end;
}

.action-btn{
  border:0;
  border-radius:9px;
  background:#00A6B8;
  color:#ffffff;
  font-family:inherit;
  font-size:15px;
  font-weight:700;
  padding:11px 20px;
  cursor:pointer;
}

.action-btn:hover{
  background:#078A9A;
}

/* EMPAREJAMIENTO */

.match-intro{
  margin-bottom:16px;
  font-size:16px;
  color:#526B76;
}

.match-list{
  display:grid;
  gap:10px;
}

.match-row{
  display:grid;
  grid-template-columns:1fr 180px;
  gap:14px;
  align-items:center;
  padding:13px 14px;
  border:1px solid #D6E6E9;
  border-radius:10px;
  background:#ffffff;
}

.match-text{
  font-size:15px;
  line-height:1.45;
  color:#314753;
}

.match-select{
  width:100%;
  padding:10px 9px;
  border:1.5px solid #BED8DE;
  border-radius:8px;
  background:#ffffff;
  font-family:inherit;
  font-size:14px;
  color:#0B2B3D;
}

.match-select.wrong{
  border:2px solid #E54B4B;
  background:#FFF5F5;
}

.match-select.correct{
  border:2px solid #2A9D71;
  background:#F1FBF6;
}

.check-area{
  margin-top:20px;
  display:flex;
  justify-content:flex-end;
}

/* FINAL */

.finish{
  text-align:center;
  padding:28px 10px;
}

.finish-icon{
  width:58px;
  height:58px;
  border-radius:50%;
  margin:0 auto 16px;
  background:#00B3C7;
  color:#ffffff;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:28px;
  font-weight:700;
}

.finish h2{
  margin:0 0 10px;
  font-size:24px;
}

.finish p{
  max-width:650px;
  margin:0 auto 22px;
  font-size:16px;
  line-height:1.55;
  color:#526B76;
}

/* RESPONSIVE */

@media(max-width:700px){

  body{
    padding:4px;
  }

  .cover{
    padding:32px 20px 34px;
  }

  .cover h1{
    font-size:24px;
  }

  .cover h2{
    font-size:19px;
  }

  .content{
    padding:20px 16px 26px;
  }

  .question{
    font-size:18px;
  }

  .line{
    width:24px;
  }

  .match-row{
    grid-template-columns:1fr;
  }

}

</style>
</head>

<body>

<div class="activity">

  <!-- PORTADA -->

  <div class="screen active" id="cover">

    <div class="cover">

      <div class="cover-icon">?</div>

      <h1>De un prompt básico a una interacción útil</h1>

      <h2>
        ¿Cómo convertir una primera solicitud en una interacción más estratégica con IA?
      </h2>

      <p>
        Revise cada situación y seleccione o empareje la respuesta que considere más adecuada.
        Si su elección no es correcta, consulte la retroalimentación e inténtelo nuevamente.
        <strong>Avanzará cuando encuentre la respuesta adecuada.</strong>
      </p>

      <div class="cover-topics">
        Formular &nbsp;&middot;&nbsp; Cuestionar &nbsp;&middot;&nbsp; Verificar &nbsp;&middot;&nbsp; Estructurar
      </div>

      <button class="action-btn" onclick="startActivity()">
        Comenzar →
      </button>

    </div>

  </div>


  <!-- PROGRESO -->

  <div class="progress" id="progress">

    <div class="step active" id="step1">1</div>
    <div class="line"></div>

    <div class="step" id="step2">2</div>
    <div class="line"></div>

    <div class="step" id="step3">3</div>
    <div class="line"></div>

    <div class="step" id="step4">4</div>

  </div>


  <div class="content" id="content" style="display:none;">


    <!-- PREGUNTA 1 -->

    <div class="screen active" id="q1">

      <p class="kicker">Pregunta 1</p>

      <p class="question">
        Un diseñador instruccional escribe el siguiente prompt:
      </p>

      <div class="context">
        “Diseñe una actividad para enseñar liderazgo.”
      </div>

      <p class="question small">
        ¿Cuál de las siguientes opciones es el mejor prompt para solicitud?
      </p>

      <div class="options">

        <button class="option" onclick="answer(1,'A',this)">
          <strong>A.</strong>
          Diseñe una actividad para enseñar liderazgo. Sea creativo, innovador y detallado.
        </button>

        <button class="option" onclick="answer(1,'B',this)">
          <strong>B.</strong>
          Actúe como experto en liderazgo y proponga una actividad interesante para estudiantes.
        </button>

        <button class="option" onclick="answer(1,'C',this)">
          <strong>C.</strong>
          Estoy diseñando una formación virtual para supervisores recién promovidos que necesitan practicar conversaciones de retroalimentación. Proponga tres actividades de máximo 30 minutos que requieran analizar situaciones y justificar una decisión.
        </button>

        <button class="option" onclick="answer(1,'D',this)">
          <strong>D.</strong>
          Diseñe cinco actividades sobre liderazgo e incluya introducción, objetivos, metodología, recursos, evaluación y conclusiones.
        </button>

      </div>

      <div class="feedback" id="feedback1"></div>
      <div class="actions" id="actions1"></div>

    </div>


    <!-- PREGUNTA 2 -->

    <div class="screen" id="q2">

      <p class="kicker">Pregunta 2</p>

      <p class="question">
        La IA propone tres actividades para una formación virtual. Las propuestas parecen adecuadas, pero el diseñador no está seguro de si realmente responden al propósito de aprendizaje.
      </p>

      <p class="question small">
        ¿Cuál sería la acción más pertinente?
      </p>

      <div class="options">

        <button class="option" onclick="answer(2,'A',this)">
          <strong>A.</strong>
          Solicitar que compare las propuestas, identifique fortalezas, debilidades y supuestos, y luego revisarlas con criterios pedagógicos.
        </button>

        <button class="option" onclick="answer(2,'B',this)">
          <strong>B.</strong>
          Elegir la propuesta que esté mejor redactada y desarrollarla.
        </button>

        <button class="option" onclick="answer(2,'C',this)">
          <strong>C.</strong>
          Pedir a la IA que amplíe las tres propuestas con más información.
        </button>

        <button class="option" onclick="answer(2,'D',this)">
          <strong>D.</strong>
          Utilizar las tres propuestas para evitar descartar una alternativa potencialmente útil.
        </button>

      </div>

      <div class="feedback" id="feedback2"></div>
      <div class="actions" id="actions2"></div>

    </div>


    <!-- PREGUNTA 3 -->

    <div class="screen" id="q3">

      <p class="kicker">Pregunta 3</p>

      <p class="question">
        Al justificar una actividad, la IA incluye la siguiente afirmación:
      </p>

      <div class="context">
        “Esta estrategia aumenta en un 40 % la retención del aprendizaje y es especialmente efectiva en adultos.”
      </div>

      <p class="question small">
        ¿Qué debería hacer el diseñador antes de utilizar esta información?
      </p>

      <div class="options">

        <button class="option" onclick="answer(3,'A',this)">
          <strong>A.</strong>
          Mantenerla porque el dato es específico y fortalece la justificación.
        </button>

        <button class="option" onclick="answer(3,'B',this)">
          <strong>B.</strong>
          Pedir a la IA que explique con mayor detalle por qué se obtiene ese porcentaje.
        </button>

        <button class="option" onclick="answer(3,'C',this)">
          <strong>C.</strong>
          Eliminar la actividad porque contiene información generada por IA.
        </button>

        <button class="option" onclick="answer(3,'D',this)">
          <strong>D.</strong>
          Verificar el dato y su fuente antes de incorporarlo al contenido o utilizarlo para justificar la decisión de diseño.
        </button>

      </div>

      <div class="feedback" id="feedback3"></div>
      <div class="actions" id="actions3"></div>

    </div>


    <!-- PREGUNTA 4 -->

    <div class="screen" id="q4">

      <p class="kicker">Pregunta 4</p>

      <p class="question">
        Ayude a estructurar un mejor prompt
      </p>

      <div class="context">
        Estoy diseñando una formación virtual para supervisores recién promovidos que necesitan practicar cómo conducir conversaciones de retroalimentación. Actúe como especialista en Diseño Instruccional para formación de adultos. Tome como referencia actividades basadas en situaciones profesionales en las que el participante deba analizar alternativas antes de decidir. Proponga tres actividades para practicar conversaciones de retroalimentación. Cada actividad debe durar un máximo de 20 minutos, poder realizarse de forma virtual y requerir que el participante justifique una decisión. Después de generar las propuestas, compárelas, identifique posibles debilidades y recomiende cuál sería más pertinente.
      </div>

      <p class="match-intro">
        Empareje cada fragmento del prompt con el componente de <strong>CRETA+R</strong> que representa.
      </p>

      <div class="match-list">

        <div class="match-row">
          <div class="match-text">
            “Estoy diseñando una formación virtual para supervisores recién promovidos que necesitan practicar cómo conducir conversaciones de retroalimentación.”
          </div>

          <select class="match-select" data-answer="Contexto">
            <option value="">Seleccione</option>
            <option>Contexto</option>
            <option>Rol</option>
            <option>Ejemplo</option>
            <option>Tarea</option>
            <option>Ajustar</option>
            <option>Refinar</option>
          </select>
        </div>


        <div class="match-row">
          <div class="match-text">
            “Actúe como especialista en Diseño Instruccional para formación de adultos.”
          </div>

          <select class="match-select" data-answer="Rol">
            <option value="">Seleccione</option>
            <option>Contexto</option>
            <option>Rol</option>
            <option>Ejemplo</option>
            <option>Tarea</option>
            <option>Ajustar</option>
            <option>Refinar</option>
          </select>
        </div>


        <div class="match-row">
          <div class="match-text">
            “Tome como referencia actividades basadas en situaciones profesionales en las que el participante deba analizar alternativas antes de decidir.”
          </div>

          <select class="match-select" data-answer="Ejemplo">
            <option value="">Seleccione</option>
            <option>Contexto</option>
            <option>Rol</option>
            <option>Ejemplo</option>
            <option>Tarea</option>
            <option>Ajustar</option>
            <option>Refinar</option>
          </select>
        </div>


        <div class="match-row">
          <div class="match-text">
            “Proponga tres actividades para practicar conversaciones de retroalimentación.”
          </div>

          <select class="match-select" data-answer="Tarea">
            <option value="">Seleccione</option>
            <option>Contexto</option>
            <option>Rol</option>
            <option>Ejemplo</option>
            <option>Tarea</option>
            <option>Ajustar</option>
            <option>Refinar</option>
          </select>
        </div>


        <div class="match-row">
          <div class="match-text">
            “Cada actividad debe durar un máximo de 20 minutos, poder realizarse de forma virtual y requerir que el participante justifique una decisión.”
          </div>

          <select class="match-select" data-answer="Ajustar">
            <option value="">Seleccione</option>
            <option>Contexto</option>
            <option>Rol</option>
            <option>Ejemplo</option>
            <option>Tarea</option>
            <option>Ajustar</option>
            <option>Refinar</option>
          </select>
        </div>


        <div class="match-row">
          <div class="match-text">
            “Después de generar las propuestas, compárelas, identifique posibles debilidades y recomiende cuál sería más pertinente.”
          </div>

          <select class="match-select" data-answer="Refinar">
            <option value="">Seleccione</option>
            <option>Contexto</option>
            <option>Rol</option>
            <option>Ejemplo</option>
            <option>Tarea</option>
            <option>Ajustar</option>
            <option>Refinar</option>
          </select>
        </div>

      </div>

      <div class="check-area">
        <button class="action-btn" onclick="checkMatching()">
          Comprobar
        </button>
      </div>

      <div class="feedback" id="feedback4"></div>
      <div class="actions" id="actions4"></div>

    </div>


    <!-- FINAL -->

    <div class="screen" id="finish">

      <div class="finish">

        <div class="finish-icon">✓</div>

        <h2>Actividad completada</h2>

        <p>
          Ha revisado cómo formular instrucciones más útiles, cuestionar una primera respuesta, verificar información y reconocer los componentes de CRETA+R dentro de una interacción.
        </p>

        <button class="action-btn" onclick="restartActivity()">
          Volver a realizar
        </button>

      </div>

    </div>

  </div>

</div>


<script>

const correctAnswers = {
  1: "C",
  2: "A",
  3: "D"
};

const correctFeedback = {

  1:
  "La solicitud incorpora información relevante sobre los participantes, el contexto, la tarea y las condiciones que orientan la respuesta.",

  2:
  "La primera respuesta es un punto de partida. Cuestionar y comparar las propuestas permite revisarlas antes de tomar una decisión.",

  3:
  "Un dato específico debe verificarse antes de utilizarlo como fundamento de una decisión o incorporarlo al contenido."

};

const wrongFeedback = {

  1:
  "Revise qué información ayuda realmente a comprender la situación. Un prompt más largo no necesariamente es mejor; debe aportar información relevante para orientar la respuesta.",

  2:
  "Antes de seleccionar o ampliar una propuesta, conviene analizar sus fortalezas, limitaciones y relación con el propósito de aprendizaje.",

  3:
  "La claridad o precisión aparente de una respuesta no garantiza su veracidad. Los datos que sustentan una decisión deben comprobarse."

};


function startActivity(){

  document.getElementById("cover").classList.remove("active");

  document.getElementById("progress").classList.add("show");

  document.getElementById("content").style.display = "block";

  document.getElementById("q1").classList.add("active");

  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}


function answer(questionNumber, selected, button){

  const screen = document.getElementById("q" + questionNumber);
  const buttons = screen.querySelectorAll(".option");

  buttons.forEach(btn => {
    btn.disabled = true;
  });

  const feedback = document.getElementById("feedback" + questionNumber);
  const actions = document.getElementById("actions" + questionNumber);

  feedback.className = "feedback show";
  actions.className = "actions show";


  if(selected === correctAnswers[questionNumber]){

    button.classList.add("correct");

    feedback.classList.add("correct");

    feedback.innerHTML =
      "<strong>Correcto.</strong> " +
      correctFeedback[questionNumber];

    actions.innerHTML =
      '<button class="action-btn" onclick="nextQuestion(' +
      questionNumber +
      ')">Continuar →</button>';

  }else{

    button.classList.add("wrong");

    feedback.classList.add("wrong");

    feedback.innerHTML =
      "<strong>Revise su respuesta.</strong> " +
      wrongFeedback[questionNumber];

    actions.innerHTML =
      '<button class="action-btn" onclick="retryQuestion(' +
      questionNumber +
      ')">Intentar de nuevo</button>';

  }

}


function retryQuestion(questionNumber){

  const screen = document.getElementById("q" + questionNumber);

  const buttons = screen.querySelectorAll(".option");

  buttons.forEach(btn => {
    btn.disabled = false;
    btn.classList.remove("wrong","correct");
  });

  const feedback = document.getElementById("feedback" + questionNumber);
  const actions = document.getElementById("actions" + questionNumber);

  feedback.className = "feedback";
  feedback.innerHTML = "";

  actions.className = "actions";
  actions.innerHTML = "";

}


function nextQuestion(current){

  document.getElementById("q" + current).classList.remove("active");

  const step = document.getElementById("step" + current);

  if(step){
    step.classList.remove("active");
    step.classList.add("done");
  }


  if(current < 4){

    const next = current + 1;

    document.getElementById("q" + next).classList.add("active");

    document.getElementById("step" + next).classList.add("active");

  }else{

    document.getElementById("progress").classList.remove("show");

    document.getElementById("finish").classList.add("active");

  }


  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}


function checkMatching(){

  const selects = document.querySelectorAll("#q4 .match-select");

  let allSelected = true;
  let allCorrect = true;


  selects.forEach(select => {

    select.classList.remove("wrong","correct");

    if(select.value === ""){
      allSelected = false;
      allCorrect = false;
      return;
    }


    if(select.value === select.dataset.answer){

      select.classList.add("correct");

    }else{

      select.classList.add("wrong");
      allCorrect = false;

    }

  });


  const feedback = document.getElementById("feedback4");
  const actions = document.getElementById("actions4");


  if(!allSelected){

    feedback.className = "feedback wrong show";

    feedback.innerHTML =
      "<strong>Complete todos los emparejamientos.</strong> Revise cada fragmento antes de comprobar.";

    return;

  }


  if(allCorrect){

    feedback.className = "feedback correct show";

    feedback.innerHTML =
      "<strong>Correcto.</strong> Cada componente cumple una función diferente dentro de la interacción. CRETA+R ayuda a organizar la información relevante, pero no obliga a utilizar siempre todos sus elementos.";

    actions.className = "actions show";

    actions.innerHTML =
      '<button class="action-btn" onclick="nextQuestion(4)">Finalizar →</button>';


    selects.forEach(select => {
      select.disabled = true;
    });


  }else{

    feedback.className = "feedback wrong show";

    feedback.innerHTML =
      "<strong>Revise los elementos marcados.</strong> Piense qué fragmentos sitúan el contexto, definen la perspectiva, muestran una referencia, establecen la tarea, fijan condiciones o permiten continuar mejorando la respuesta.";

    actions.className = "actions show";

    actions.innerHTML =
      '<button class="action-btn" onclick="retryMatching()">Intentar de nuevo</button>';

  }

}


function retryMatching(){

  const selects = document.querySelectorAll("#q4 .match-select");

  selects.forEach(select => {

    select.disabled = false;
    select.classList.remove("wrong","correct");

  });

  const feedback = document.getElementById("feedback4");
  const actions = document.getElementById("actions4");

  feedback.className = "feedback";
  feedback.innerHTML = "";

  actions.className = "actions";
  actions.innerHTML = "";

}


function restartActivity(){

  document.querySelectorAll(".screen").forEach(screen => {
    screen.classList.remove("active");
  });


  document.getElementById("cover").classList.add("active");

  document.getElementById("progress").classList.remove("show");

  document.getElementById("content").style.display = "none";


  document.querySelectorAll(".step").forEach(step => {
    step.classList.remove("active","done");
  });

  document.getElementById("step1").classList.add("active");


  for(let q=1; q<=3; q++){

    const screen = document.getElementById("q" + q);

    screen.querySelectorAll(".option").forEach(btn => {

      btn.disabled = false;
      btn.classList.remove("wrong","correct");

    });

    document.getElementById("feedback" + q).className = "feedback";
    document.getElementById("feedback" + q).innerHTML = "";

    document.getElementById("actions" + q).className = "actions";
    document.getElementById("actions" + q).innerHTML = "";

  }


  document.querySelectorAll("#q4 .match-select").forEach(select => {

    select.value = "";
    select.disabled = false;
    select.classList.remove("wrong","correct");

  });


  document.getElementById("feedback4").className = "feedback";
  document.getElementById("feedback4").innerHTML = "";

  document.getElementById("actions4").className = "actions";
  document.getElementById("actions4").innerHTML = "";


  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}

</script>

</body>
</html>

```

## AF1-3-brief.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Del contexto al brief</title>

<style>

*{
  box-sizing:border-box;
}

html,body{
  margin:0;
  padding:0;
  background:#ffffff;
  font-family:Poppins,Arial,sans-serif;
  color:#0B2B3D;
}

body{
  padding:24px;
}

.wrap{
  max-width:920px;
  margin:0 auto;
}

/* PORTADA */

.cover{
  text-align:center;
  padding:36px 24px 30px;
}

.cover h1{
  margin:0 0 14px;
  font-size:30px;
  line-height:1.2;
  color:#0B2B3D;
}

.cover p{
  margin:0 auto 20px;
  max-width:690px;
  font-size:17px;
  line-height:1.6;
  color:#526B76;
}

/* BOTONES */

.btn{
  border:0;
  border-radius:8px;
  background:#00B3C7;
  color:#ffffff;
  padding:12px 24px;
  font-family:inherit;
  font-size:16px;
  font-weight:700;
  cursor:pointer;
}

.btn:hover{
  opacity:.9;
}

/* PROGRESO */

.progress{
  display:none;
  justify-content:center;
  gap:9px;
  margin:0 0 24px;
}

.step{
  width:34px;
  height:34px;
  border-radius:50%;
  border:1.5px solid #C6DCE1;
  background:#F8FCFD;
  color:#526B76;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:14px;
  font-weight:700;
}

.step.active{
  background:#00B3C7;
  border-color:#00B3C7;
  color:#ffffff;
}

.step.done{
  background:#2D8692;
  border-color:#2D8692;
  color:#ffffff;
}

/* PREGUNTAS */

.card{
  display:none;
  border:1px solid #DCE6E9;
  border-radius:12px;
  padding:26px;
  background:#ffffff;
}

.card.active{
  display:block;
}

.question-number{
  font-size:14px;
  font-weight:700;
  color:#2D8692;
  margin-bottom:8px;
}

.card h2{
  margin:0 0 16px;
  font-size:22px;
  line-height:1.35;
  color:#0B2B3D;
}

.case{
  background:#F4FAFB;
  border-left:4px solid #62BED3;
  padding:16px 18px;
  margin:0 0 20px;
  font-size:16px;
  line-height:1.55;
}

/* OPCIONES */

.options{
  display:grid;
  gap:10px;
}

.option{
  width:100%;
  text-align:left;
  border:1.5px solid #D6EEF2;
  border-radius:8px;
  background:#F8FCFD;
  color:#0B2B3D;
  padding:13px 15px;
  font-family:inherit;
  font-size:15px;
  line-height:1.45;
  cursor:pointer;
}

.option:hover{
  border-color:#00B3C7;
}

.option.correct{
  border-color:#2D8692;
  background:#EAF7F9;
}

.option.wrong{
  border-color:#C54B4B;
  background:#FFF4F4;
}

/* RETROALIMENTACIÓN */

.feedback{
  display:none;
  margin-top:16px;
  padding:14px 16px;
  border-radius:8px;
  font-size:15px;
  line-height:1.5;
}

.feedback.correct{
  display:block;
  background:#EAF7F9;
  border:1px solid #B9DEE3;
}

.feedback.wrong{
  display:block;
  background:#FFF4F4;
  border:1px solid #E8BABA;
}

.next{
  display:none;
  margin-top:18px;
  text-align:right;
}

/* EMPAREJAMIENTO */

.match-grid{
  display:grid;
  gap:14px;
}

.match-item{
  border:1px solid #DCE6E9;
  border-radius:9px;
  padding:15px;
  background:#F8FCFD;
}

.match-item p{
  margin:0 0 10px;
  font-size:15px;
  line-height:1.45;
}

.match-item select{
  width:100%;
  padding:10px;
  border:1px solid #C6DCE1;
  border-radius:7px;
  font-family:inherit;
  font-size:15px;
  color:#0B2B3D;
  background:#ffffff;
}

/* CIERRE */

.finish{
  display:none;
  text-align:center;
  padding:40px 24px;
  border:1px solid #D6EEF2;
  border-radius:12px;
  background:#F8FCFD;
}

.finish h2{
  margin:0 0 14px;
  font-size:26px;
}

.finish p{
  margin:0 auto;
  max-width:700px;
  font-size:16px;
  line-height:1.6;
  color:#526B76;
}

/* RESPONSIVE */

@media(max-width:650px){

  body{
    padding:14px;
  }

  .cover{
    padding:24px 12px;
  }

  .cover h1{
    font-size:25px;
  }

  .card{
    padding:18px;
  }

}

</style>
</head>

<body>

<div class="wrap">

<!-- PORTADA -->

<div class="cover" id="cover">

  <h1>Del contexto al brief</h1>

  <p>
    Revise c&oacute;mo distinguir evidencia y supuestos, utilizar la IA para analizar
    informaci&oacute;n y tomar decisiones antes de consolidar el brief de un proyecto.
  </p>

  <button class="btn" type="button" onclick="startActivity()">
    Comenzar
  </button>

</div>


<!-- PROGRESO -->

<div class="progress" id="progress">

  <div class="step active" id="step1">1</div>
  <div class="step" id="step2">2</div>
  <div class="step" id="step3">3</div>
  <div class="step" id="step4">4</div>

</div>


<!-- PREGUNTA 1 -->

<div class="card" id="q1">

  <div class="question-number">
    Pregunta 1 de 4
  </div>

  <h2>
    &iquest;Dato o supuesto?
  </h2>

  <div class="case">

    Durante una reuni&oacute;n inicial, el responsable del proyecto comenta:

    <br><br>

    <strong>
      &ldquo;Creo que los nuevos supervisores tienen dificultades para dar
      retroalimentaci&oacute;n porque les falta confianza.&rdquo;
    </strong>

    <br><br>

    Todav&iacute;a no se han realizado entrevistas ni se cuenta con
    informaci&oacute;n que confirme esa explicaci&oacute;n.

  </div>

  <div class="options">

    <button class="option" type="button" onclick="answer(1,'A',this)">
      A. Como evidencia, porque proviene del responsable del proyecto.
    </button>

    <button class="option" type="button" onclick="answer(1,'B',this)">
      B. Como una necesidad confirmada que puede incorporarse al brief.
    </button>

    <button class="option" type="button" onclick="answer(1,'C',this)">
      C. Como un supuesto que necesita contrastarse con evidencia.
    </button>

    <button class="option" type="button" onclick="answer(1,'D',this)">
      D. Como informaci&oacute;n que debe descartarse porque no proviene de los participantes.
    </button>

  </div>

  <div class="feedback" id="feedback1"></div>

  <div class="next" id="next1">

    <button class="btn" type="button" onclick="nextQuestion(1)">
      Continuar
    </button>

  </div>

</div>


<!-- PREGUNTA 2 -->

<div class="card" id="q2">

  <div class="question-number">
    Pregunta 2 de 4
  </div>

  <h2>
    Analizar una entrevista con IA
  </h2>

  <div class="case">

    Despu&eacute;s de una entrevista con el responsable de un proyecto,
    el dise&ntilde;ador obtiene la transcripci&oacute;n completa.

    <br><br>

    &iquest;Cu&aacute;l ser&iacute;a el uso m&aacute;s pertinente de la IA en este momento?

  </div>

  <div class="options">

    <button class="option" type="button" onclick="answer(2,'A',this)">
      A. Pedir que identifique necesidades, patrones, restricciones y aspectos
      que requieren validaci&oacute;n, trabajando con la informaci&oacute;n de la transcripci&oacute;n.
    </button>

    <button class="option" type="button" onclick="answer(2,'B',this)">
      B. Pedir que construya directamente el perfil completo de los participantes
      para ahorrar tiempo.
    </button>

    <button class="option" type="button" onclick="answer(2,'C',this)">
      C. Solicitar que dise&ntilde;e las actividades del curso a partir de la entrevista.
    </button>

    <button class="option" type="button" onclick="answer(2,'D',this)">
      D. Pedir que complete la informaci&oacute;n que el responsable no pudo proporcionar.
    </button>

  </div>

  <div class="feedback" id="feedback2"></div>

  <div class="next" id="next2">

    <button class="btn" type="button" onclick="nextQuestion(2)">
      Continuar
    </button>

  </div>

</div>


<!-- PREGUNTA 3 -->

<div class="card" id="q3">

  <div class="question-number">
    Pregunta 3 de 4
  </div>

  <h2>
    Antes de cerrar el brief
  </h2>

  <div class="case">

    Un dise&ntilde;ador prepara este brief preliminar:

    <br><br>

    <strong>Necesidad:</strong> mejorar la comunicaci&oacute;n de los supervisores.<br>
    <strong>Participantes:</strong> supervisores reci&eacute;n promovidos.<br>
    <strong>Modalidad:</strong> virtual.<br>
    <strong>Duraci&oacute;n:</strong> 2 horas.<br>
    <strong>Resultado esperado:</strong> conducir conversaciones de retroalimentaci&oacute;n de forma efectiva.

    <br><br>

    Sin embargo, todav&iacute;a no sabe qu&eacute; dificultades presentan actualmente
    los supervisores ni qu&eacute; evidencia respalda la necesidad.

  </div>

  <div class="options">

    <button class="option" type="button" onclick="answer(3,'A',this)">
      A. Pedir a la IA que complete las caracter&iacute;sticas que probablemente tengan los supervisores.
    </button>

    <button class="option" type="button" onclick="answer(3,'B',this)">
      B. Comenzar el dise&ntilde;o porque ya cuenta con los elementos principales.
    </button>

    <button class="option" type="button" onclick="answer(3,'C',this)">
      C. Transformar inmediatamente el resultado esperado en actividades.
    </button>

    <button class="option" type="button" onclick="answer(3,'D',this)">
      D. Registrar los vac&iacute;os de informaci&oacute;n e identificar qu&eacute; necesita investigar o validar.
    </button>

  </div>

  <div class="feedback" id="feedback3"></div>

  <div class="next" id="next3">

    <button class="btn" type="button" onclick="nextQuestion(3)">
      Continuar
    </button>

  </div>

</div>


<!-- PREGUNTA 4 -->

<div class="card" id="q4">

  <div class="question-number">
    Pregunta 4 de 4
  </div>

  <h2>
    &iquest;Qu&eacute; hacer con las observaciones de la IA?
  </h2>

  <p style="font-size:16px; line-height:1.55; margin:0 0 18px;">
    El dise&ntilde;ador pide a la IA una segunda revisi&oacute;n de su brief.
    Seleccione la decisi&oacute;n profesional m&aacute;s adecuada para cada observaci&oacute;n.
  </p>

  <div class="match-grid">

    <div class="match-item">

      <p>
        <strong>1.</strong>
        &ldquo;Los registros proporcionados muestran baja participaci&oacute;n
        en las actividades de pr&aacute;ctica.&rdquo;
      </p>

      <select id="match1">
        <option value="">Seleccione...</option>
        <option value="aceptar">Aceptar</option>
        <option value="modificar">Modificar / validar</option>
        <option value="descartar">Descartar</option>
      </select>

    </div>


    <div class="match-item">

      <p>
        <strong>2.</strong>
        &ldquo;La baja participaci&oacute;n podr&iacute;a estar relacionada con la duraci&oacute;n
        de las actividades, pero ser&iacute;a necesario comprobarlo.&rdquo;
      </p>

      <select id="match2">
        <option value="">Seleccione...</option>
        <option value="aceptar">Aceptar</option>
        <option value="modificar">Modificar / validar</option>
        <option value="descartar">Descartar</option>
      </select>

    </div>


    <div class="match-item">

      <p>
        <strong>3.</strong>
        &ldquo;Los participantes seguramente tienen poca experiencia tecnol&oacute;gica.&rdquo;
        No existe informaci&oacute;n que lo respalde.
      </p>

      <select id="match3">
        <option value="">Seleccione...</option>
        <option value="aceptar">Aceptar</option>
        <option value="modificar">Modificar / validar</option>
        <option value="descartar">Descartar</option>
      </select>

    </div>

  </div>

  <div style="margin-top:18px;">

    <button class="btn" type="button" onclick="checkMatching()">
      Comprobar
    </button>

  </div>

  <div class="feedback" id="feedback4"></div>

  <div class="next" id="next4">

    <button class="btn" type="button" onclick="finishActivity()">
      Finalizar
    </button>

  </div>

</div>


<!-- CIERRE -->

<div class="finish" id="finish">

  <h2>
    Actividad completada
  </h2>

  <p>
    Ha revisado c&oacute;mo distinguir evidencia y supuestos, analizar informaci&oacute;n
    con apoyo de IA, reconocer vac&iacute;os y valorar cr&iacute;ticamente sus observaciones
    antes de consolidar un brief.
  </p>

</div>

</div>


<script>

/* RESPUESTAS CORRECTAS */

const correctAnswers = {
  1:"C",
  2:"A",
  3:"D"
};


/* RETROALIMENTACIÓN CORRECTA */

const correctFeedback = {

  1:
  "Correcto. La afirmación puede orientar el análisis, pero todavía no cuenta con evidencia suficiente para tratarla como un hecho del proyecto.",

  2:
  "Correcto. La IA puede ayudar a organizar y analizar la evidencia disponible sin convertir los vacíos de información en datos del proyecto.",

  3:
  "Correcto. Un brief puede contener información pendiente. Lo importante es hacer visibles esos vacíos en lugar de completarlos con supuestos."

};


/* RETROALIMENTACIÓN DE REINTENTO */

const wrongFeedback = {

  1:
  "Revise la diferencia entre una posible explicación y una afirmación que ya está respaldada por evidencia.",

  2:
  "En esta etapa todavía estamos comprendiendo el proyecto. La IA puede apoyar el análisis de la evidencia, pero no debería inventar información ni adelantar decisiones de diseño.",

  3:
  "El brief no necesita tener todas las respuestas, pero sí debe mostrar qué información está respaldada y qué todavía requiere validación."

};


/* INICIAR */

function startActivity(){

  document.getElementById("cover").style.display="none";

  document.getElementById("progress").style.display="flex";

  document.getElementById("q1").classList.add("active");

  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}


/* RESPONDER PREGUNTAS 1-3 */

function answer(question,selected,button){

  const feedback =
    document.getElementById("feedback"+question);

  const next =
    document.getElementById("next"+question);


  document
  .querySelectorAll("#q"+question+" .option")
  .forEach(function(option){

    option.classList.remove("wrong");
    option.classList.remove("correct");

  });


  if(selected===correctAnswers[question]){

    button.classList.add("correct");

    feedback.className =
      "feedback correct";

    feedback.innerHTML =
      correctFeedback[question];

    next.style.display =
      "block";


    document
    .querySelectorAll("#q"+question+" .option")
    .forEach(function(option){

      option.disabled=true;

    });

  }

  else{

    button.classList.add("wrong");

    feedback.className =
      "feedback wrong";

    feedback.innerHTML =
      wrongFeedback[question];

    next.style.display =
      "none";

  }

}


/* SIGUIENTE PREGUNTA */

function nextQuestion(current){

  const currentCard =
    document.getElementById("q"+current);

  currentCard.classList.remove("active");


  document
  .getElementById("step"+current)
  .classList.remove("active");

  document
  .getElementById("step"+current)
  .classList.add("done");


  const next =
    current+1;


  document
  .getElementById("q"+next)
  .classList.add("active");


  document
  .getElementById("step"+next)
  .classList.add("active");


  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}


/* PREGUNTA 4 */

function checkMatching(){

  const a =
    document.getElementById("match1").value;

  const b =
    document.getElementById("match2").value;

  const c =
    document.getElementById("match3").value;


  const feedback =
    document.getElementById("feedback4");

  const next =
    document.getElementById("next4");


  if(
    a==="aceptar" &&
    b==="modificar" &&
    c==="descartar"
  ){

    feedback.className =
      "feedback correct";

    feedback.innerHTML =
      "Correcto. Las observaciones de la IA no se incorporan automáticamente. El diseñador debe valorar cuáles están respaldadas, cuáles requieren validación y cuáles se basan en supuestos no sustentados.";

    next.style.display =
      "block";


    document.getElementById("match1").disabled=true;
    document.getElementById("match2").disabled=true;
    document.getElementById("match3").disabled=true;

  }

  else{

    feedback.className =
      "feedback wrong";

    feedback.innerHTML =
      "Revise la relación de cada afirmación con la evidencia disponible. Una observación respaldada puede incorporarse; una interpretación puede requerir validación y un supuesto sin evidencia puede descartarse.";

    next.style.display =
      "none";

  }

}


/* FINALIZAR */

function finishActivity(){

  document
  .getElementById("q4")
  .classList.remove("active");


  document
  .getElementById("step4")
  .classList.remove("active");

  document
  .getElementById("step4")
  .classList.add("done");


  document
  .getElementById("finish")
  .style.display="block";


  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}

</script>

</body>
</html>

```

## CI1-3-brief.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>CI1-5-brief</title>

<style>

*{
  box-sizing:border-box;
}

html,
body{
  margin:0;
  padding:0;
  background:#ffffff;
  font-family:Poppins, Arial, sans-serif;
  color:#0B2B3D;
}

.wrap{
  max-width:1000px;
  margin:0 auto;
}

.tabs{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:8px;
  margin:0 0 5px 0;
}

.tab{
  border:1.5px solid #C6DCE1;
  border-radius:8px;
  background:#F8FCFD;
  color:#0B2B3D;
  padding:8px 6px;
  min-height:40px;
  font-family:inherit;
  font-size:15px;
  font-weight:700;
  cursor:pointer;
}

.tab:hover{
  border-color:#00B3C7;
}

.tab.active{
  background:#00B3C7;
  border-color:#00B3C7;
  color:#ffffff;
}

.detail{
  margin:0;
  padding:5px 10px 2px;
  font-size:15px;
  line-height:1.35;
  color:#526B76;
}

.detail strong{
  color:#0B2B3D;
}

@media(max-width:650px){

  .tabs{
    grid-template-columns:repeat(2,1fr);
  }

  .tab{
    font-size:14px;
  }

}

</style>
</head>

<body>

<div class="wrap">

  <div class="tabs">

    <button class="tab active" type="button" onclick="showInfo('necesidad',this)">
      Necesidad
    </button>

    <button class="tab" type="button" onclick="showInfo('evidencia',this)">
      Evidencia
    </button>

    <button class="tab" type="button" onclick="showInfo('vacios',this)">
      Vacíos
    </button>

    <button class="tab" type="button" onclick="showInfo('decisiones',this)">
      Decisiones
    </button>

  </div>


  <div class="detail" id="detail">
    <strong>Necesidad:</strong> ¿Está claro qué problema, necesidad o situación origina el proyecto?
  </div>

</div>


<script>

const content = {

  necesidad:
  "<strong>Necesidad:</strong> ¿Está claro qué problema, necesidad o situación origina el proyecto?",

  evidencia:
  "<strong>Evidencia:</strong> ¿Qué datos, documentos, registros o testimonios respaldan lo que se afirma?",

  vacios:
  "<strong>Vacíos:</strong> ¿Qué información todavía falta o requiere validación?",

  decisiones:
  "<strong>Decisiones:</strong> ¿Qué elementos ya pueden utilizarse como base para avanzar y cuáles todavía no?"

};


function showInfo(key,button){

  document.querySelectorAll(".tab").forEach(function(tab){
    tab.classList.remove("active");
  });

  button.classList.add("active");

  document.getElementById("detail").innerHTML =
    content[key];

}

</script>

</body>
</html>

```

## CI1-3-certeza.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>CI1-3-certeza</title>

<style>

*{
  box-sizing:border-box;
}

html,
body{
  margin:0;
  padding:0;
  background:#ffffff;
  font-family:Poppins, Arial, sans-serif;
  color:#0B2B3D;
}

.wrap{
  max-width:1000px;
  margin:0 auto;
}

.tabs{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:8px;
  margin:0 0 5px 0;
}

.tab{
  border:1.5px solid #C6DCE1;
  border-radius:8px;
  background:#F8FCFD;
  color:#0B2B3D;
  padding:8px 6px;
  min-height:40px;
  font-family:inherit;
  font-size:15px;
  font-weight:700;
  cursor:pointer;
  transition:.15s ease;
}

.tab:hover{
  border-color:#00B3C7;
}

.tab.active{
  background:#00B3C7;
  border-color:#00B3C7;
  color:#ffffff;
}

.detail{
  margin:0;
  padding:5px 10px 2px;
  font-size:15px;
  line-height:1.35;
  color:#526B76;
}

.detail strong{
  color:#0B2B3D;
}

@media(max-width:650px){

  .tabs{
    grid-template-columns:repeat(2,1fr);
  }

  .tab{
    font-size:14px;
  }

}

</style>
</head>

<body>

<div class="wrap">

  <div class="tabs">

    <button class="tab active" type="button" onclick="showInfo('se',this)">
      Sé
    </button>

    <button class="tab" type="button" onclick="showInfo('infiero',this)">
      Infiero
    </button>

    <button class="tab" type="button" onclick="showInfo('supongo',this)">
      Supongo
    </button>

    <button class="tab" type="button" onclick="showInfo('investigar',this)">
      Necesito investigar
    </button>

  </div>

  <div class="detail" id="detail">
    <strong>Sé:</strong> Tengo evidencia, datos o información disponible que respalda este dato.
  </div>

</div>


<script>

const content = {

  se:
  "<strong>Sé:</strong> Tengo evidencia, datos o información disponible que respalda este dato.",

  infiero:
  "<strong>Infiero:</strong> Lo interpreto a partir de la evidencia disponible.",

  supongo:
  "<strong>Supongo:</strong> Lo estoy dando por cierto, pero todavía no cuento con evidencia suficiente.",

  investigar:
  "<strong>Necesito investigar:</strong> Debo recopilar o validar esta información antes de utilizarla para tomar una decisión."

};


function showInfo(key,button){

  document.querySelectorAll(".tab").forEach(function(tab){
    tab.classList.remove("active");
  });

  button.classList.add("active");

  document.getElementById("detail").innerHTML =
    content[key];

}

</script>

</body>
</html>

```

## CI2-1-escalas-diseno.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CI2-1-escalas-diseno</title>
<style>
*{box-sizing:border-box;}
html,body{margin:0;padding:0;background:#ffffff;font-family:Poppins,Arial,sans-serif;color:#0B2B3D;}
.wrap{max-width:1000px;margin:0 auto;padding:2px;}
.intro{font-size:15px;line-height:1.45;color:#526B76;margin:0 0 12px 0;}
.cards{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:12px;}
.card{border:1.5px solid #C6DCE1;border-radius:10px;background:#F8FCFD;color:#0B2B3D;padding:14px 12px;min-height:78px;font-family:inherit;text-align:left;cursor:pointer;transition:.18s ease;position:relative;}
.card:hover{border-color:#00B3C7;transform:translateY(-1px);}
.card.active{background:#0B2B3D;border-color:#0B2B3D;color:#ffffff;}
.card .kicker{display:block;font-size:12px;font-weight:700;letter-spacing:.4px;text-transform:uppercase;color:#2D8692;margin-bottom:4px;}
.card.active .kicker{color:#62BED3;}
.card .title{display:block;font-size:17px;font-weight:700;line-height:1.2;}
.card .hint{display:block;font-size:13px;line-height:1.3;color:#607985;margin-top:5px;}
.card.active .hint{color:#D6EEF2;}
.panel{display:none;border:1px solid #D6EEF2;border-radius:10px;background:#FFFFFF;overflow:hidden;box-shadow:0 3px 12px rgba(11,43,61,.06);animation:fadeIn .2s ease;}
.panel.active{display:block;}
.panel-head{background:#F4FAFB;border-bottom:1px solid #D6EEF2;padding:13px 16px;}
.panel-head strong{font-size:16px;color:#0B2B3D;}
.flow{display:grid;grid-template-columns:1fr 28px 1fr 28px 1fr;align-items:stretch;padding:14px;gap:6px;}
.block{border:1px solid #DCE6E9;border-radius:9px;background:#F8FCFD;padding:13px 14px;min-height:132px;}
.block .label{display:inline-block;font-size:12px;font-weight:700;letter-spacing:.3px;text-transform:uppercase;color:#2D8692;margin-bottom:6px;}
.block p{font-size:14px;line-height:1.45;margin:0;color:#35505C;}
.arrow{display:flex;align-items:center;justify-content:center;font-size:25px;font-weight:700;color:#00B3C7;}
.note{margin:0 14px 14px;padding:11px 13px;border-left:4px solid #00B3C7;background:#F5FBFC;font-size:13.5px;line-height:1.4;color:#526B76;}
@keyframes fadeIn{from{opacity:0;transform:translateY(3px)}to{opacity:1;transform:translateY(0)}}
@media(max-width:760px){
  .cards{grid-template-columns:1fr;}
  .flow{grid-template-columns:1fr;}
  .arrow{transform:rotate(90deg);height:22px;}
  .block{min-height:auto;}
}
</style>
</head>
<body>
<div class="wrap">
  <p class="intro">Seleccione una escala para observar cómo cambia el alcance del resultado, la evidencia y la experiencia.</p>

  <div class="cards">
    <button class="card active" type="button" onclick="showPanel('curso',this)">
      <span class="kicker">Escala 1</span>
      <span class="title">Curso</span>
      <span class="hint">Resultado amplio e integrador</span>
    </button>

    <button class="card" type="button" onclick="showPanel('unidad',this)">
      <span class="kicker">Escala 2</span>
      <span class="title">Unidad / módulo</span>
      <span class="hint">Resultado específico dentro del curso</span>
    </button>

    <button class="card" type="button" onclick="showPanel('experiencia',this)">
      <span class="kicker">Escala 3</span>
      <span class="title">Tema / experiencia</span>
      <span class="hint">Desempeño puntual y observable</span>
    </button>
  </div>

  <div class="panel active" id="curso">
    <div class="panel-head"><strong>Ejemplo: curso de formación docente</strong></div>
    <div class="flow">
      <div class="block">
        <span class="label">Resultado</span>
        <p>Diseñar experiencias de aprendizaje coherentes con los resultados esperados, el contexto y las características de los participantes.</p>
      </div>
      <div class="arrow">→</div>
      <div class="block">
        <span class="label">Evidencia</span>
        <p>Proyecto integrador de diseño instruccional que articula resultados, evidencias, experiencias, recursos y criterios de evaluación.</p>
      </div>
      <div class="arrow">→</div>
      <div class="block">
        <span class="label">Experiencia</span>
        <p>Desarrollo progresivo de un proyecto, análisis de casos, revisión entre pares, prototipado y mejora a partir de retroalimentación.</p>
      </div>
    </div>
    <div class="note"><strong>Observe:</strong> a nivel de curso, la evidencia y la experiencia suelen ser más amplias e integradoras.</div>
  </div>

  <div class="panel" id="unidad">
    <div class="panel-head"><strong>Ejemplo: unidad sobre evaluación formativa</strong></div>
    <div class="flow">
      <div class="block">
        <span class="label">Resultado</span>
        <p>Diseñar una estrategia de retroalimentación formativa para una actividad de aprendizaje, considerando las características de los estudiantes.</p>
      </div>
      <div class="arrow">→</div>
      <div class="block">
        <span class="label">Evidencia</span>
        <p>Propuesta de estrategia de retroalimentación acompañada de una breve justificación de las decisiones tomadas.</p>
      </div>
      <div class="arrow">→</div>
      <div class="block">
        <span class="label">Experiencia</span>
        <p>Analizar situaciones de retroalimentación, comparar alternativas y diseñar una propuesta aplicable a un caso específico.</p>
      </div>
    </div>
    <div class="note"><strong>Observe:</strong> en una unidad o módulo, el resultado se acota y la evidencia permite demostrar un desempeño más específico.</div>
  </div>

  <div class="panel" id="experiencia">
    <div class="panel-head"><strong>Ejemplo: experiencia de aprendizaje sobre análisis de conflictos</strong></div>
    <div class="flow">
      <div class="block">
        <span class="label">Resultado</span>
        <p>Analizar alternativas para resolver un conflicto laboral y justificar la decisión más adecuada según el contexto.</p>
      </div>
      <div class="arrow">→</div>
      <div class="block">
        <span class="label">Evidencia</span>
        <p>Análisis breve de un caso con comparación de alternativas y justificación de la decisión seleccionada.</p>
      </div>
      <div class="arrow">→</div>
      <div class="block">
        <span class="label">Experiencia</span>
        <p>Examinar un conflicto, identificar posibles respuestas, contrastar consecuencias y tomar una decisión argumentada.</p>
      </div>
    </div>
    <div class="note"><strong>Observe:</strong> en una experiencia puntual, resultado, evidencia y actividad pueden vincularse de manera muy directa.</div>
  </div>
</div>
<script>
function showPanel(id,button){
  document.querySelectorAll('.card').forEach(function(card){card.classList.remove('active');});
  document.querySelectorAll('.panel').forEach(function(panel){panel.classList.remove('active');});
  button.classList.add('active');
  document.getElementById(id).classList.add('active');
}
</script>
</body>
</html>

```

## CI2-1-bonus-resultado.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CI2-1-bonus-resultado</title>
<style>
*{box-sizing:border-box;}
html,body{margin:0;padding:0;background:#ffffff;font-family:Poppins,Arial,sans-serif;color:#0B2B3D;}
.wrap{max-width:1000px;margin:0 auto;padding:2px;}
.accordion{border:1px solid #D6EEF2;border-radius:10px;overflow:hidden;background:#F8FCFD;}
.trigger{width:100%;border:0;background:#F4FAFB;color:#0B2B3D;padding:14px 18px;font-family:inherit;display:flex;align-items:center;justify-content:space-between;gap:14px;cursor:pointer;text-align:left;}
.trigger:hover{background:#EEF8FA;}
.trigger-left{display:flex;align-items:center;gap:12px;}
.badge{display:inline-flex;align-items:center;justify-content:center;min-width:86px;height:28px;padding:0 10px;border-radius:999px;background:#2D8692;color:#fff;font-size:12px;font-weight:700;letter-spacing:.4px;text-transform:uppercase;}
.title-group{display:flex;flex-direction:column;gap:2px;}
.title{font-size:17px;font-weight:700;line-height:1.3;}
.hint{font-size:12.5px;font-weight:400;color:#607985;line-height:1.25;}
.arrow{font-size:22px;color:#00B3C7;transition:transform .2s ease;line-height:1;}
.trigger.open .arrow{transform:rotate(180deg);}
.content{display:none;padding:18px;background:#FFFFFF;border-top:1px solid #D6EEF2;}
.content.open{display:block;animation:fadeIn .2s ease;}
.content p{font-size:15px;line-height:1.55;color:#35505C;margin:0 0 15px 0;}
.structure{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin:14px 0 16px 0;}
.item{border:1px solid #DCE6E9;border-radius:8px;background:#F8FCFD;padding:12px 10px;min-height:98px;}
.item strong{display:block;font-size:14px;color:#0B2B3D;margin-bottom:5px;}
.item span{font-size:13.5px;line-height:1.4;color:#526B76;}
.ai-box{border-left:4px solid #00B3C7;background:#F5FBFC;padding:13px 15px;margin-top:8px;}
.ai-box p{font-size:14px;line-height:1.5;margin:0;color:#35505C;}
@keyframes fadeIn{from{opacity:0;transform:translateY(-2px)}to{opacity:1;transform:translateY(0)}}
@media(max-width:760px){
  .structure{grid-template-columns:repeat(2,1fr);}
  .badge{display:none;}
  .title{font-size:16px;}
  .hint{font-size:12px;}
}
</style>
</head>
<body>
<div class="wrap">
  <div class="accordion">
    <button class="trigger" type="button" id="trigger" aria-expanded="false" onclick="toggleAccordion()">
      <span class="trigger-left">
        <span class="badge">Bonus track</span>
        <span class="title-group">
          <span class="title">¿Está bien formulado el resultado?</span>
          <span class="hint">Haga clic para descubrirlo</span>
        </span>
      </span>
      <span class="arrow">⌄</span>
    </button>

    <div class="content" id="content">
      <p><strong>Antes de utilizar la IA para generar evidencias o experiencias, conviene comprobar que el resultado de aprendizaje expresa con suficiente claridad el desempeño esperado.</strong> Si el resultado es ambiguo, las propuestas que genere la IA también pueden partir de una dirección poco precisa.</p>

      <p>Una forma práctica de revisarlo es verificar cuatro componentes. No se trata de convertir el resultado en una fórmula rígida, sino de comprobar si ofrece información suficiente para orientar las siguientes decisiones de diseño.</p>

      <div class="structure">
        <div class="item">
          <strong>Verbo</strong>
          <span>¿Qué acción o desempeño realizará el participante?</span>
        </div>
        <div class="item">
          <strong>Objeto</strong>
          <span>¿Sobre qué contenido, problema, producto o situación actuará?</span>
        </div>
        <div class="item">
          <strong>Contexto</strong>
          <span>¿En qué situación, condiciones o escenario deberá realizarlo?</span>
        </div>
        <div class="item">
          <strong>Criterio</strong>
          <span>¿Qué condición o nivel permitirá valorar que el desempeño es adecuado?</span>
        </div>
      </div>

      <div class="ai-box">
        <p><strong>Use la IA como revisora.</strong> Pídale que identifique términos ambiguos, señale información que falta o proponga reformulaciones sin cambiar la intención del resultado. Después, revise las alternativas y decida qué cambios conservar.</p>
      </div>
    </div>
  </div>
</div>
<script>
function toggleAccordion(){
  var trigger=document.getElementById('trigger');
  var content=document.getElementById('content');
  var isOpen=content.classList.contains('open');
  content.classList.toggle('open');
  trigger.classList.toggle('open');
  trigger.setAttribute('aria-expanded', String(!isOpen));
}
</script>
</body>
</html>

```

## CI2-1-auditar-criterios.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CI2-1 Criterios de auditoría</title>
<style>
*{box-sizing:border-box}
html,body{margin:0;padding:0;background:#fff;font-family:Poppins,Arial,sans-serif;color:#0B2B3D}
.wrap{max-width:1000px;margin:0 auto;padding:4px}
.intro{font-size:15px;line-height:1.5;color:#526B76;margin:0 0 14px}
.cards{display:grid;grid-template-columns:repeat(4,1fr);gap:9px;margin-bottom:12px}
.card{border:1.5px solid #C6DCE1;border-radius:10px;background:#F8FCFD;padding:13px 11px;font-family:inherit;text-align:left;cursor:pointer;transition:.18s ease;min-height:98px}
.card:hover{border-color:#00B3C7;transform:translateY(-1px)}
.card:focus{outline:3px solid rgba(0,179,199,.22);outline-offset:2px}
.card.active{background:#2D8692;border-color:#2D8692;color:#fff}
.card strong{display:block;font-size:15px;line-height:1.2;margin-bottom:6px}
.card span{display:block;font-size:12.5px;line-height:1.35;color:#607985}
.card.active span{color:#EAF7F9}
.panel{border:1px solid #D6EEF2;border-radius:10px;background:#fff;padding:15px 16px;animation:fade .2s ease}
.panel h3{font-size:18px;margin:0 0 7px;color:#0B2B3D}
.question{font-size:15px;line-height:1.5;color:#35505C;margin:0 0 12px}
.detail{background:#E7F7F9;border:1px solid #62BED3;border-radius:9px;padding:11px 13px}
.detail strong{display:block;font-size:13.5px;margin-bottom:4px;color:#0B2B3D}
.detail p{font-size:13.5px;line-height:1.45;color:#35505C;margin:0}
@keyframes fade{from{opacity:0;transform:translateY(2px)}to{opacity:1;transform:translateY(0)}}
@media(max-width:760px){.cards{grid-template-columns:repeat(2,1fr)}}
@media(max-width:420px){.cards{grid-template-columns:1fr}}
</style>
</head>
<body>
<div class="wrap">
  <p class="intro">Haga clic en cada criterio para revisar una dimensión distinta de la relación entre resultado, evidencia y experiencias de aprendizaje.</p>
  <div class="cards" role="group" aria-label="Criterios de auditoría">
    <button class="card active" type="button" data-key="alineacion"><strong>Alineación</strong><span>Resultado ↔ evidencia</span></button>
    <button class="card" type="button" data-key="preparacion"><strong>Preparación</strong><span>Experiencias ↔ evidencia</span></button>
    <button class="card" type="button" data-key="progresion"><strong>Progresión</strong><span>Complejidad y apoyos</span></button>
    <button class="card" type="button" data-key="factibilidad"><strong>Factibilidad</strong><span>Tiempo, recursos y condiciones</span></button>
  </div>
  <div id="panel" class="panel" aria-live="polite"></div>
</div>
<script>
const data={
  alineacion:{
    title:'Alineación',
    q:'¿La evidencia permite demostrar realmente el resultado de aprendizaje?',
    d:'Revise si la evidencia hace visible la acción o desempeño expresado en el resultado y si alguna parte importante queda fuera.'
  },
  preparacion:{
    title:'Preparación',
    q:'¿Las experiencias permiten practicar lo que después se solicitará en la evidencia?',
    d:'Compruebe que el participante tenga oportunidades suficientes para desarrollar y practicar los conocimientos, decisiones y desempeños requeridos.'
  },
  progresion:{
    title:'Progresión',
    q:'¿La secuencia avanza con una complejidad adecuada y con los apoyos necesarios?',
    d:'Busque saltos de dificultad, prácticas demasiado tempranas o apoyos que desaparecen antes de que el participante pueda actuar con mayor autonomía.'
  },
  factibilidad:{
    title:'Factibilidad',
    q:'¿El diseño puede realizarse con el tiempo, los recursos y las condiciones disponibles?',
    d:'Contraste la propuesta con la modalidad, duración, carga de trabajo, recursos y restricciones definidas para el proyecto.'
  }
};
const cards=[...document.querySelectorAll('.card')];
const panel=document.getElementById('panel');
function showItem(key,btn){
  cards.forEach(x=>{x.classList.remove('active');x.setAttribute('aria-pressed','false')});
  btn.classList.add('active');
  btn.setAttribute('aria-pressed','true');
  const d=data[key];
  panel.innerHTML=`<h3>${d.title}</h3><p class="question">${d.q}</p><div class="detail"><strong>Qué conviene observar</strong><p>${d.d}</p></div>`;
}
cards.forEach(btn=>btn.addEventListener('click',()=>showItem(btn.dataset.key,btn)));
cards.forEach(btn=>btn.setAttribute('aria-pressed','false'));
showItem('alineacion',cards[0]);
</script>
</body>
</html>
```

## AF2-1-evidencia-auditoria.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AF2-1 Del resultado a la auditoría</title>
<style>
*{box-sizing:border-box}
html,body{margin:0;padding:0;background:#F4FAFB;font-family:Poppins,Arial,sans-serif;color:#0B2B3D}
body{padding:8px}
.activity{max-width:1000px;margin:0 auto;background:#fff;border:1px solid #D6EEF2;border-radius:14px;overflow:hidden}
.screen{display:none}.screen.active{display:block}
.cover{padding:44px 40px 46px;text-align:center}
.cover-icon{width:62px;height:62px;border-radius:50%;margin:0 auto 20px;background:#00B3C7;color:#fff;display:flex;align-items:center;justify-content:center;font-size:30px;font-weight:700}
.cover h1{margin:0 0 8px;font-size:27px;line-height:1.25;color:#0B2B3D}
.cover h2{margin:0 auto 20px;max-width:700px;font-size:21px;line-height:1.4;font-weight:500;color:#078A9A}
.cover p{max-width:760px;margin:0 auto 22px;font-size:16px;line-height:1.6;color:#526B76}
.cover-topics{max-width:720px;margin:0 auto 26px;padding:13px 20px;background:#F4FAFB;border:1px solid #D6EEF2;border-radius:10px;font-size:16px;font-weight:600;color:#0B2B3D}
.btn{border:0;border-radius:9px;background:#00A6B8;color:#fff;padding:11px 20px;font-family:inherit;font-size:15px;font-weight:700;cursor:pointer}.btn:hover{background:#078A9A}.btn.secondary{background:#EAF8F8;color:#087D8D;border:1px solid #B7E4E6}
.content{padding:26px 34px 32px}
.kicker{margin:0 0 8px;text-align:center;color:#078A9A;text-transform:uppercase;letter-spacing:.7px;font-size:13px;font-weight:700}
.title{margin:0 auto 10px;text-align:center;font-size:22px;line-height:1.35;color:#0B2B3D}
.instructions{max-width:850px;margin:0 auto 22px;text-align:center;font-size:15.5px;line-height:1.6;color:#526B76}
.bank{background:#F8FCFD;border:1px solid #D6EEF2;border-radius:12px;padding:16px;margin-bottom:18px}
.bank-title{margin:0 0 12px;font-size:15px;font-weight:700;color:#0B2B3D;text-align:center}
.cards{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px}
.card{width:100%;min-width:0;background:#fff;border:1.5px solid #C6DCE1;border-radius:11px;padding:13px 14px 13px 44px;cursor:grab;font-size:14px;line-height:1.45;color:#284551;position:relative;overflow-wrap:anywhere;word-break:normal;white-space:normal;box-shadow:0 2px 7px rgba(11,43,61,.04)}
.card:before{content:attr(data-letter);position:absolute;left:13px;top:13px;width:22px;height:22px;border-radius:50%;background:#EAF8F8;color:#078A9A;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700}.card:hover{border-color:#00B3C7;background:#FCFEFE}.card.dragging{opacity:.45}
.top-zones{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:14px;margin-bottom:14px}.bottom-zone{margin-bottom:18px}.zone{border-radius:12px;overflow:hidden;background:#fff}.zone.result{border:2px solid #47B8C8}.zone.evidence{border:2px solid #E7A34B}.zone.audit{border:2px solid #8D79C8}
.zone-head{padding:13px 15px;display:flex;align-items:center;gap:10px;color:#fff}.result .zone-head{background:#2D9EAD}.evidence .zone-head{background:#D58A2D}.audit .zone-head{background:#735FB4}.zone-title{font-size:16px;font-weight:700}.zone-question{font-size:12.5px;line-height:1.35;opacity:.95;margin-top:2px}
.icon{width:32px;height:32px;border-radius:50%;background:rgba(255,255,255,.18);display:flex;align-items:center;justify-content:center;font-weight:700;flex:0 0 auto}
.drop-area{padding:12px;display:flex;flex-direction:column;gap:9px;min-height:148px;background:#fff}.audit .drop-area{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));align-content:start;min-height:125px}.drop-area.over{background:#F7FBFC}.placeholder{width:100%;border:1.5px dashed #CEDDE1;border-radius:9px;padding:14px 12px;text-align:center;color:#7A919B;font-size:13px;line-height:1.4;margin:auto 0}.audit .placeholder{grid-column:1/-1}
.zone .card{font-size:13.5px;line-height:1.42;padding-top:12px;padding-bottom:12px}.correct{border:2px solid #55AE72!important;background:#F2FBF5!important}.incorrect{border:2px solid #D96B6B!important;background:#FFF5F5!important}
.actions{display:flex;gap:10px;justify-content:center;margin:18px 0 14px}.feedback{display:none;max-width:850px;margin:0 auto 14px;border-radius:10px;padding:14px 16px;font-size:14.5px;line-height:1.5}.feedback.ok{display:block;background:#F0FAF5;border:1px solid #B7DFC9;color:#17633F}.feedback.error{display:block;background:#FFF3F3;border:1px solid #F1BBBB;color:#932F2F}.closing{max-width:820px;margin:0 auto;text-align:center;font-size:14.5px;line-height:1.55;color:#526B76;padding:4px 12px 6px}.closing strong{color:#0B2B3D}
@media(max-width:760px){.cover{padding:32px 20px 34px}.cover h1{font-size:24px}.cover h2{font-size:19px}.content{padding:22px 16px 28px}.cards,.top-zones,.audit .drop-area{grid-template-columns:1fr}.drop-area{min-height:120px}}
</style>
</head>
<body>
<div class="activity">
  <div class="screen active" id="cover">
    <div class="cover">
      <div class="cover-icon">↕</div>
      <h1>Del resultado a la auditoría</h1>
      <h2>Clasifique antes de decidir</h2>
      <p>Arrastre cada tarjeta según la función que cumple dentro del diseño. Distinga entre el resultado de aprendizaje, la evidencia que permite demostrarlo y la instrucción que utilizaría para pedir a la IA una revisión crítica.</p>
      <div class="cover-topics">Resultado &nbsp;&middot;&nbsp; Evidencia &nbsp;&middot;&nbsp; Auditoría con IA</div>
      <button class="btn" onclick="startActivity()">Comenzar →</button>
    </div>
  </div>

  <div class="screen" id="activityScreen">
    <div class="content">
      <p class="kicker">Actividad formativa 2.1</p>
      <h2 class="title">Clasifique cada tarjeta</h2>
      <p class="instructions">Arrastre cada tarjeta al espacio que corresponda. Lea la frase completa antes de moverla: unas expresan lo que el participante deberá hacer al finalizar, otras describen la evidencia que permitirá observar ese aprendizaje y otras son instrucciones dirigidas a la IA para revisar la coherencia.</p>

      <div class="bank">
        <div class="bank-title">Tarjetas para clasificar</div>
        <div class="cards" id="cardBank">
          <div class="card" draggable="true" data-type="resultado" data-letter="A">Analizar alternativas para resolver un conflicto laboral y justificar la decisión más adecuada.</div>
          <div class="card" draggable="true" data-type="evidencia" data-letter="B">Análisis de un caso con comparación de alternativas y justificación de una decisión.</div>
          <div class="card" draggable="true" data-type="auditoria" data-letter="C">Revisa si esta evidencia realmente permite demostrar el resultado y señala posibles desajustes.</div>
          <div class="card" draggable="true" data-type="resultado" data-letter="D">Proponer una mejora pertinente a partir del análisis de una situación de desempeño.</div>
          <div class="card" draggable="true" data-type="evidencia" data-letter="E">Propuesta argumentada de mejora basada en la situación analizada y en criterios definidos.</div>
          <div class="card" draggable="true" data-type="auditoria" data-letter="F">Identifica supuestos, vacíos de información y aspectos del contexto que conviene revisar antes de aceptar la propuesta.</div>
        </div>
      </div>

      <div class="top-zones">
        <div class="zone result">
          <div class="zone-head"><div class="icon">R</div><div><div class="zone-title">Resultado</div><div class="zone-question">¿Qué deberá ser capaz de hacer?</div></div></div>
          <div class="drop-area" data-zone="resultado"><div class="placeholder">Arrastre aquí los resultados de aprendizaje.</div></div>
        </div>
        <div class="zone evidence">
          <div class="zone-head"><div class="icon">E</div><div><div class="zone-title">Evidencia</div><div class="zone-question">¿Qué permitirá demostrarlo?</div></div></div>
          <div class="drop-area" data-zone="evidencia"><div class="placeholder">Arrastre aquí las evidencias de aprendizaje.</div></div>
        </div>
      </div>

      <div class="bottom-zone">
        <div class="zone audit">
          <div class="zone-head"><div class="icon">IA</div><div><div class="zone-title">Auditar con IA</div><div class="zone-question">¿Qué instrucción utilizaría para revisar?</div></div></div>
          <div class="drop-area" data-zone="auditoria"><div class="placeholder">Arrastre aquí las instrucciones para cuestionar o revisar la propuesta con IA.</div></div>
        </div>
      </div>

      <div class="actions"><button class="btn" id="checkBtn">Validar</button><button class="btn secondary" id="resetBtn">Reintentar</button></div>
      <div id="feedbackBox" class="feedback"></div>
      <div class="closing"><strong>Idea clave:</strong> un resultado expresa una acción o desempeño esperado; la evidencia permite observarlo y la auditoría con IA ayuda a cuestionar la coherencia antes de decidir.</div>
    </div>
  </div>
</div>
<script>
function startActivity(){document.getElementById('cover').classList.remove('active');document.getElementById('activityScreen').classList.add('active');}
const cards=document.querySelectorAll('.card');const dropAreas=document.querySelectorAll('.drop-area');const bank=document.getElementById('cardBank');const feedbackBox=document.getElementById('feedbackBox');let draggedCard=null;
function refreshPlaceholders(){dropAreas.forEach(area=>{const p=area.querySelector('.placeholder');const real=Array.from(area.children).filter(el=>el.classList.contains('card'));if(p)p.style.display=real.length?'none':'block';});}
cards.forEach(card=>{card.addEventListener('dragstart',()=>{draggedCard=card;setTimeout(()=>card.classList.add('dragging'),0)});card.addEventListener('dragend',()=>{card.classList.remove('dragging');draggedCard=null});});
bank.addEventListener('dragover',e=>e.preventDefault());bank.addEventListener('drop',e=>{e.preventDefault();if(draggedCard){bank.appendChild(draggedCard);refreshPlaceholders();}});
dropAreas.forEach(area=>{area.addEventListener('dragover',e=>{e.preventDefault();area.classList.add('over')});area.addEventListener('dragleave',()=>area.classList.remove('over'));area.addEventListener('drop',e=>{e.preventDefault();area.classList.remove('over');if(draggedCard){area.appendChild(draggedCard);refreshPlaceholders();}})});
function clearMarks(){document.querySelectorAll('.card').forEach(c=>c.classList.remove('correct','incorrect'));feedbackBox.className='feedback';feedbackBox.innerHTML='';}
document.getElementById('checkBtn').addEventListener('click',()=>{clearMarks();let placed=0,correct=0;dropAreas.forEach(area=>{const type=area.dataset.zone;Array.from(area.children).filter(el=>el.classList.contains('card')).forEach(card=>{placed++;if(card.dataset.type===type){card.classList.add('correct');correct++;}else card.classList.add('incorrect');});});const total=document.querySelectorAll('.card').length;if(placed<total){feedbackBox.className='feedback error';feedbackBox.innerHTML='<strong>Aún faltan tarjetas.</strong> Complete las tres categorías antes de validar.';return;}if(correct===total){feedbackBox.className='feedback ok';feedbackBox.innerHTML='<strong>Muy bien.</strong> Distinguió correctamente resultados de aprendizaje, evidencias e instrucciones para auditar con IA.';}else{feedbackBox.className='feedback error';feedbackBox.innerHTML='<strong>Revise las tarjetas marcadas.</strong> Resultado = acción o desempeño esperado; evidencia = forma de demostrarlo; auditoría = instrucción para revisar con IA.';}});
document.getElementById('resetBtn').addEventListener('click',()=>{clearMarks();Array.from(document.querySelectorAll('.card')).sort((a,b)=>a.dataset.letter.localeCompare(b.dataset.letter)).forEach(c=>bank.appendChild(c));refreshPlaceholders();});
refreshPlaceholders();
</script>
</body>
</html>
```


# Unidad 2

## CI2-2-prompt-vs-asistente.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prompt vs Asistente de IA</title>
<style>
*{box-sizing:border-box}
html,body{margin:0;padding:0;background:#fff;font-family:Poppins,Arial,sans-serif;color:#0B2B3D}
.wrap{max-width:1000px;margin:0 auto;padding:4px}
.intro{font-size:15px;line-height:1.5;color:#526B76;margin:0 0 14px}
.tabs{display:grid;grid-template-columns:repeat(3,1fr);gap:9px;margin-bottom:12px}
.tab{border:1.5px solid #C6DCE1;border-radius:10px;background:#F8FCFD;padding:12px 10px;cursor:pointer;font-family:inherit;text-align:left;min-height:82px}
.tab.active{background:#2D8692;border-color:#2D8692;color:#fff}
.tab strong{display:block;font-size:15px;margin-bottom:4px}
.tab span{font-size:12.5px;line-height:1.35;color:#607985}
.tab.active span{color:#EAF7F9}
.panel{border:1px solid #D6EEF2;border-radius:10px;padding:15px 16px;background:#fff}
.cols{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.card{border-radius:10px;padding:14px;border:1px solid #D6EEF2;background:#F4FAFB}
.card.example{background:#E7F7F9;border-color:#62BED3}
.card h3{font-size:16px;margin:0 0 7px}
.card p{font-size:13.5px;line-height:1.5;color:#35505C;margin:0}
.note{margin-top:10px;border-left:5px solid #00B3C7;padding:11px 13px;background:#fff;font-size:13.5px;line-height:1.45;color:#35505C}
@media(max-width:700px){.tabs,.cols{grid-template-columns:1fr}}
</style>
</head>
<body>
<div class="wrap">
  <p class="intro">Explore tres situaciones para decidir cuándo basta un prompt y cuándo puede aportar más valor un asistente de IA.</p>
  <div class="tabs" role="group" aria-label="Situaciones de uso">
    <button class="tab active" type="button" data-key="puntual"><strong>Tarea puntual</strong><span>Una necesidad concreta</span></button>
    <button class="tab" type="button" data-key="recurrente"><strong>Tarea recurrente</strong><span>Mismos criterios, varias veces</span></button>
    <button class="tab" type="button" data-key="cambiante"><strong>Tarea cambiante</strong><span>Contexto y criterios variables</span></button>
  </div>
  <div id="panel" class="panel" aria-live="polite"></div>
</div>
<script>
const data={
  puntual:{
    prompt:'Pedir tres alternativas de evidencia para un resultado específico.',
    assistant:'Crear un asistente sería innecesario si la tarea se resolverá una sola vez.',
    decision:'Aquí suele bastar un prompt claro y contextualizado.'
  },
  recurrente:{
    prompt:'Repetir cada vez el contexto, los criterios de revisión y los límites.',
    assistant:'Mantener una función estable para revisar propuestas usando los mismos criterios y restricciones.',
    decision:'Aquí un asistente puede ahorrar repetición y aportar consistencia.'
  },
  cambiante:{
    prompt:'Adaptar la instrucción a cada proyecto, contexto o necesidad nueva.',
    assistant:'Podría quedar demasiado rígido si sus criterios cambian constantemente.',
    decision:'Aquí conviene valorar si realmente existe una función suficientemente estable como para reutilizarla.'
  }
};
const tabs=[...document.querySelectorAll('.tab')];
const panel=document.getElementById('panel');
function show(key,btn){
  tabs.forEach(x=>x.classList.remove('active'));
  btn.classList.add('active');
  const d=data[key];
  panel.innerHTML=`<div class="cols"><div class="card"><h3>Con un prompt</h3><p>${d.prompt}</p></div><div class="card example"><h3>Con un asistente</h3><p>${d.assistant}</p></div></div><div class="note"><strong>Decisión:</strong> ${d.decision}</div>`;
}
tabs.forEach(btn=>btn.addEventListener('click',()=>show(btn.dataset.key,btn)));
show('puntual',tabs[0]);
</script>
</body>
</html>
```

## CI2-2-configurar-asistente.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Configurar asistente de IA</title>
<style>
*{box-sizing:border-box}
html,body{margin:0;padding:0;background:#fff;font-family:Poppins,Arial,sans-serif;color:#0B2B3D}
.wrap{max-width:1000px;margin:0 auto;padding:4px}
.intro{font-size:15px;line-height:1.5;color:#526B76;margin:0 0 14px}
.grid{display:grid;grid-template-columns:repeat(2,1fr);gap:10px;margin-bottom:12px}
.field{background:#F4FAFB;border:1px solid #D6EEF2;border-radius:10px;padding:12px}
.field label{display:block;font-size:14px;font-weight:700;margin-bottom:6px}
.field textarea{width:100%;min-height:88px;resize:vertical;border:1px solid #BFD8DF;border-radius:8px;padding:10px;font-family:inherit;font-size:14px;color:#0B2B3D;background:#fff}
.field textarea:focus{outline:3px solid rgba(0,179,199,.18);border-color:#00B3C7}
.actions{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:12px}
button{border:0;border-radius:8px;padding:10px 14px;font-family:inherit;font-weight:700;cursor:pointer}
.primary{background:#2D8692;color:#fff}
.secondary{background:#E7F7F9;color:#0B2B3D;border:1px solid #62BED3}
.output{border:1px solid #62BED3;background:#E7F7F9;border-radius:10px;padding:14px;display:none}
.output h3{font-size:16px;margin:0 0 8px}
.output p{font-size:13.5px;line-height:1.5;color:#35505C;margin:0 0 7px}
.empty{font-size:13.5px;color:#7A8E97;margin:0}
@media(max-width:700px){.grid{grid-template-columns:1fr}}
</style>
</head>
<body>
<div class="wrap">
  <p class="intro">Complete los cuatro elementos básicos. La ficha final le ayudará a visualizar una primera configuración antes de llevarla a la herramienta de IA que utilice.</p>
  <div class="grid">
    <div class="field"><label for="proposito">Propósito</label><textarea id="proposito" placeholder="¿Para qué existe el asistente y qué tarea debe apoyar?"></textarea></div>
    <div class="field"><label for="contexto">Contexto</label><textarea id="contexto" placeholder="¿Qué información debe considerar al responder?"></textarea></div>
    <div class="field"><label for="criterios">Criterios</label><textarea id="criterios" placeholder="¿Qué criterios o principios debe aplicar?"></textarea></div>
    <div class="field"><label for="limites">Límites</label><textarea id="limites" placeholder="¿Qué no debe asumir, inventar o decidir?"></textarea></div>
  </div>
  <div class="actions">
    <button class="primary" type="button" id="generar">Ver ficha de configuración</button>
    <button class="secondary" type="button" id="ejemplo">Cargar ejemplo</button>
    <button class="secondary" type="button" id="limpiar">Limpiar</button>
  </div>
  <div id="salida" class="output" aria-live="polite"></div>
</div>
<script>
const ids=['proposito','contexto','criterios','limites'];
const get=id=>document.getElementById(id);
const salida=get('salida');
function val(id){return get(id).value.trim()}
function render(){
  const data=ids.map(id=>val(id));
  if(data.every(x=>!x)){
    salida.style.display='block';
    salida.innerHTML='<p class="empty">Complete al menos un elemento para generar la ficha.</p>';
    return;
  }
  salida.style.display='block';
  salida.innerHTML=`<h3>Ficha de configuración</h3>
  <p><strong>Propósito:</strong> ${data[0]||'Pendiente de definir'}</p>
  <p><strong>Contexto:</strong> ${data[1]||'Pendiente de definir'}</p>
  <p><strong>Criterios:</strong> ${data[2]||'Pendiente de definir'}</p>
  <p><strong>Límites:</strong> ${data[3]||'Pendiente de definir'}</p>`;
}
get('generar').addEventListener('click',render);
get('ejemplo').addEventListener('click',()=>{
  get('proposito').value='Apoyar la revisión de propuestas de Diseño Instruccional antes de tomar decisiones.';
  get('contexto').value='Considerar participantes, modalidad, duración, recursos, restricciones y resultados definidos.';
  get('criterios').value='Revisar alineación entre resultados, evidencias y experiencias, además de pertinencia y factibilidad.';
  get('limites').value='No inventar información faltante, no modificar decisiones sin explicarlo y no asumir que toda propuesta necesita cambios.';
  render();
});
get('limpiar').addEventListener('click',()=>{
  ids.forEach(id=>get(id).value='');
  salida.style.display='none';
  salida.innerHTML='';
});
</script>
</body>
</html>
```

## CI3-2-hecho-interpretacion.html

```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hecho o interpretación</title>
<style>
  *{box-sizing:border-box}
  body{margin:0;font-family:Arial,sans-serif;background:#F8FCFD;color:#0B2B3D}
  .wrap{max-width:980px;margin:0 auto;padding:22px}
  .card{background:#fff;border:1px solid #DCE6E9;border-radius:16px;padding:22px;box-shadow:0 2px 8px rgba(11,43,61,.06)}
  h1{font-size:26px;margin:0 0 8px}
  .lead{margin:0 0 18px;line-height:1.55}
  .instructions{background:#E7F7F9;border:1px solid #62BED3;border-radius:12px;padding:14px 16px;margin-bottom:18px;line-height:1.5}
  .status{min-height:24px;margin:12px 0;font-weight:700}
  .board{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin:18px 0}
  .zone{min-height:180px;border:2px dashed #62BED3;border-radius:14px;padding:14px;background:#F4FAFB}
  .zone h2{font-size:18px;margin:0 0 10px;text-align:center}
  .items{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px;margin-top:18px}
  .item{border:1px solid #D6EEF2;border-radius:12px;background:#fff;padding:12px;cursor:grab;line-height:1.4}
  .item:focus{outline:3px solid #00B3C7;outline-offset:2px}
  .item.selected{border:2px solid #00B3C7;background:#E7F7F9}
  .placed{margin:8px 0;cursor:default}
  .correct{border-color:#2D8692;background:#F4FAFB}
  .wrong{border-color:#B85C5C;background:#FFF7F7}
  .feedback{font-size:13px;margin-top:6px;line-height:1.35}
  .actions{display:flex;flex-wrap:wrap;gap:10px;margin-top:18px}
  button{border:0;border-radius:10px;padding:10px 16px;font-weight:700;cursor:pointer}
  .primary{background:#0B2B3D;color:#fff}
  .secondary{background:#E7F7F9;color:#0B2B3D;border:1px solid #62BED3}
  .score{margin-top:16px;padding:14px 16px;border-left:5px solid #2D8692;background:#fff}
  @media(max-width:700px){.board,.items{grid-template-columns:1fr}}
</style>
</head>
<body>
<div class="wrap">
  <div class="card">
    <h1>Hecho o interpretación</h1>
    <p class="lead">Clasifique cada afirmación según corresponda. Puede arrastrarla a una categoría o seleccionarla y luego hacer clic en <strong>Hecho</strong> o <strong>Interpretación</strong>.</p>
    <div class="instructions"><strong>Propósito:</strong> practicar la diferencia entre información observable y conclusiones que requieren verificación antes de una conversación de retroalimentación.</div>

    <div id="status" class="status" aria-live="polite"></div>

    <div class="board">
      <div class="zone" id="hecho" tabindex="0" aria-label="Categoría Hecho">
        <h2>Hecho</h2>
      </div>
      <div class="zone" id="interpretacion" tabindex="0" aria-label="Categoría Interpretación">
        <h2>Interpretación</h2>
      </div>
    </div>

    <div id="items" class="items"></div>

    <div class="actions">
      <button class="secondary" id="btnHecho">Enviar a Hecho</button>
      <button class="secondary" id="btnInterpretacion">Enviar a Interpretación</button>
      <button class="primary" id="btnRevisar">Revisar respuestas</button>
      <button class="secondary" id="btnReiniciar">Reiniciar</button>
    </div>

    <div id="score" class="score" style="display:none" aria-live="polite"></div>
  </div>
</div>

<script>
const data = [
  {id:1,text:"Llegó 15 minutos tarde a la reunión.",cat:"hecho",fb:"Puede observarse y verificarse mediante la hora de llegada."},
  {id:2,text:"No está comprometido con el equipo.",cat:"interpretacion",fb:"Expresa una conclusión sobre la actitud de la persona; requiere evidencia adicional."},
  {id:3,text:"Entregó el informe dos días después de la fecha acordada.",cat:"hecho",fb:"La fecha de entrega puede comprobarse."},
  {id:4,text:"No le interesa mejorar.",cat:"interpretacion",fb:"Atribuye una intención que no ha sido verificada."},
  {id:5,text:"Interrumpió tres veces durante la conversación.",cat:"hecho",fb:"Describe un comportamiento observable y cuantificable."},
  {id:6,text:"Está a la defensiva.",cat:"interpretacion",fb:"Es una valoración del comportamiento, no un dato directamente verificable."},
  {id:7,text:"No respondió dos mensajes enviados durante la semana.",cat:"hecho",fb:"Puede comprobarse revisando los mensajes enviados y las respuestas."},
  {id:8,text:"No valora las opiniones de los demás.",cat:"interpretacion",fb:"Generaliza una intención o actitud a partir de una interpretación."}
];

let selected=null;
const placements={};

function makeItem(d){
  const el=document.createElement("div");
  el.className="item";
  el.draggable=true;
  el.tabIndex=0;
  el.dataset.id=d.id;
  el.textContent=d.text;
  el.addEventListener("dragstart",e=>e.dataTransfer.setData("text/plain",d.id));
  el.addEventListener("click",()=>selectItem(el,d.id));
  el.addEventListener("keydown",e=>{
    if(e.key==="Enter"||e.key===" "){e.preventDefault();selectItem(el,d.id);}
  });
  return el;
}

function selectItem(el,id){
  document.querySelectorAll(".item").forEach(x=>x.classList.remove("selected"));
  selected=id;
  el.classList.add("selected");
  document.getElementById("status").textContent="Afirmación seleccionada. Elija una categoría.";
}

function place(id,cat){
  const item=document.querySelector('.item[data-id="'+id+'"]');
  if(!item)return;
  placements[id]=cat;
  item.classList.remove("selected","correct","wrong");
  item.classList.add("placed");
  item.querySelector(".feedback")?.remove();
  document.getElementById(cat).appendChild(item);
  selected=null;
  document.getElementById("status").textContent="Afirmación ubicada en "+(cat==="hecho"?"Hecho":"Interpretación")+".";
}

["hecho","interpretacion"].forEach(cat=>{
  const zone=document.getElementById(cat);
  zone.addEventListener("dragover",e=>e.preventDefault());
  zone.addEventListener("drop",e=>{e.preventDefault();place(Number(e.dataTransfer.getData("text/plain")),cat);});
});

document.getElementById("btnHecho").onclick=()=>{if(selected)place(selected,"hecho")};
document.getElementById("btnInterpretacion").onclick=()=>{if(selected)place(selected,"interpretacion")};

document.getElementById("btnRevisar").onclick=()=>{
  let ok=0;
  data.forEach(d=>{
    const el=document.querySelector('.item[data-id="'+d.id+'"]');
    el.classList.remove("correct","wrong");
    el.querySelector(".feedback")?.remove();
    const fb=document.createElement("div");
    fb.className="feedback";
    if(placements[d.id]===d.cat){
      ok++; el.classList.add("correct");
      fb.textContent="Correcto.";
    }else{
      el.classList.add("wrong");
      fb.textContent="Revise: "+d.fb;
    }
    el.appendChild(fb);
  });
  const score=document.getElementById("score");
  score.style.display="block";
  score.innerHTML="<strong>Resultado: "+ok+" de "+data.length+"</strong><br>"+(ok===data.length?"Excelente. Distinguió correctamente hechos e interpretaciones.":"Revise las afirmaciones marcadas y vuelva a intentarlo.");
};

document.getElementById("btnReiniciar").onclick=init;

function init(){
  selected=null;
  Object.keys(placements).forEach(k=>delete placements[k]);
  const items=document.getElementById("items");
  items.innerHTML="";
  document.getElementById("hecho").querySelectorAll(".item").forEach(x=>x.remove());
  document.getElementById("interpretacion").querySelectorAll(".item").forEach(x=>x.remove());
  data.forEach(d=>items.appendChild(makeItem(d)));
  document.getElementById("score").style.display="none";
  document.getElementById("score").innerHTML="";
  document.getElementById("status").textContent="";
}
init();
</script>
</body>
</html>
```


# Unidad 3

