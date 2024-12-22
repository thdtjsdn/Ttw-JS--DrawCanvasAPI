# Ttw-JS--DrawCanvasAPI

---

# 문의 사항

- thdtjsdn@gmail.com

---

# Canvas Context의 Draw API 입니다.

- 많은 다량의 랜더링을 고려하여 성능 위주의 코드로 작성 되었습니다.

---

# 본 API는 '무료제공' 입니다.

- 자유롭게 사용하셔도 무방합니다.

---

# Example link
	- http://thdtjsdn.com:49310/app_tool/html_page/DrawCanvas/index.html

---

# Sample source

```javascript
const APIS = TAPI.w.apis.CANVASContextDraw;

const CANVAS = TAPI.ge('ID-CANVAS');
const CONTEXT = CANVAS.getContext('2d');

const EVENT_LISTENERS = {
	clear: function(){
		CONTEXT.clearRect(0, 0, CANVAS.width, CANVAS.height);
	}
	, drawArc: function () {
		
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		APIS.drawArc(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), 2, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getX_Random(), getY_Random(), getRadius_Random(), getArc_Random(), Math.PI, false);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}

	, drawCircle: function () {
		
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		APIS.drawCircle_Fill(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getX_Random(), getY_Random(), getRadius_Random());
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		APIS.drawCircle_Line(CONTEXT, 5, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getX_Random(), getY_Random(), getRadius_Random());
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}

	, drawLine: function () {
		
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		APIS.drawLine(CONTEXT, 5, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getX_Random(), getY_Random(), getX_Random(), getY_Random());
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}

	, drawLineGradient: function () {
		
		var colorStops = [
			0.0, APIS_RANDOM_HEXCOLOR(),
			0.5, APIS_RANDOM_HEXCOLOR(),
			1.0, APIS_RANDOM_HEXCOLOR()
		];

		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		APIS.drawLine_Gradient(CONTEXT, 5, 1.0, getX_Random(), getY_Random(), getX_Random(), getY_Random(), colorStops);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}

	, drawPolygon: function () {
		
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		var a = [];
		var i=0, iLen=APIS_RANDOM_NUMBER(5, 10);
		for(; i<iLen; ++i){ a.push(getX_Random(), getY_Random()); }
		APIS.drawPolygon(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), 2, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), a);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}

	, drawPolygonGradientLinear: function () {
		
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		var a = [];
		var i=0, iLen=APIS_RANDOM_NUMBER(5, 10);
		for(; i<iLen; ++i){ a.push(getX_Random(), getY_Random()); }

		var colorStops = [
			0.0, APIS_RANDOM_HEXCOLOR(),
			0.5, APIS_RANDOM_HEXCOLOR(),
			1.0, APIS_RANDOM_HEXCOLOR()
		];

		APIS.drawPolygon_Gradient_Linear(CONTEXT, getAlpha_Random(), 2, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), a, 150, 150, 350, 250, colorStops);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}
	, drawPolygonGradientLinearCenter: function () {
		
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		var a = [];
		var i=0, iLen=APIS_RANDOM_NUMBER(5, 10);
		for(; i<iLen; ++i){ a.push(getX_Random(), getY_Random()); }

		var colorStops = [
			0.0, APIS_RANDOM_HEXCOLOR(),
			0.5, APIS_RANDOM_HEXCOLOR(),
			1.0, APIS_RANDOM_HEXCOLOR()
		];

		APIS.drawPolygon_Gradient_Linear_Center(CONTEXT, getAlpha_Random(), 2, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), a, colorStops);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}

	, drawRegularPolygon: function () {
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		APIS.drawRegularPolygon(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), 1, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getX_Random(), getY_Random(), getRadius_Random(), getSides_Random());
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}

	, drawPolyline: function () {
		
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		var a = [];
		var i=0, iLen=APIS_RANDOM_NUMBER(5, 10);
		for(; i<iLen; ++i){ a.push(getX_Random(), getY_Random()); }
		APIS.drawPolyline(CONTEXT, 2, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), a);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}
	, drawPolylineGradientLinear: function () {
		
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		var a = [];
		var i=0, iLen=APIS_RANDOM_NUMBER(5, 10);
		for(; i<iLen; ++i){ a.push(getX_Random(), getY_Random()); }

		var colorStops = [
			0.0, APIS_RANDOM_HEXCOLOR(),
			0.5, APIS_RANDOM_HEXCOLOR(),
			1.0, APIS_RANDOM_HEXCOLOR()
		];

		APIS.drawPolyline_Gradient_Linear(CONTEXT, 2, getAlpha_Random(), a, 150, 150, 350, 250, colorStops);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}
	, drawPolylineGradientLinearCenter: function () {
		
		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		var a = [];
		var i=0, iLen=APIS_RANDOM_NUMBER(5, 10);
		for(; i<iLen; ++i){ a.push(getX_Random(), getY_Random()); }

		var colorStops = [
			0.0, APIS_RANDOM_HEXCOLOR(),
			0.5, APIS_RANDOM_HEXCOLOR(),
			1.0, APIS_RANDOM_HEXCOLOR()
		];

		APIS.drawPolyline_Gradient_Linear_Center(CONTEXT, 2, getAlpha_Random(), a, colorStops);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}

	, drawGradientCircular: function () {
		
		var colorStops = [
			0.0, APIS_RANDOM_HEXCOLOR(),
			0.5, APIS_RANDOM_HEXCOLOR(),
			1.0, APIS_RANDOM_HEXCOLOR()
		];

		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		APIS.drawGradient_Circular(CONTEXT, getX_Random(), getY_Random(), getRadius_Random(), getRadius_Random(), colorStops);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}

	, drawGradientLinear: function () {
		
		var colorStops = [
			0.0, APIS_RANDOM_HEXCOLOR(),
			0.5, APIS_RANDOM_HEXCOLOR(),
			1.0, APIS_RANDOM_HEXCOLOR()
		];

		if(TAPI.gec('ID-CHECKBOX--PATH-BEGIN')){ CONTEXT.beginPath(); }
		APIS.drawGradient_Linear(CONTEXT, getX_Random(), getY_Random(), getX_Random(), getY_Random(), colorStops);
		if(TAPI.gec('ID-CHECKBOX--PATH-CLOSE')){ CONTEXT.closePath(); }

		if(TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')){ requestAnimationFrame(arguments.callee); }
	}
};
```

---

# API 목록(필요할 법한 목록만)

- drawArc(context, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, cX, cY, r, sA, eA, counterClockWise)

- drawArc_Fill(context, fillStyle, globalAlpha, cX, cY, r, sA, eA, counterClockWise)

- drawArc_Line(context, lineWidth, strokeStyle, globalAlpha, cX, cY, r, sA, eA, counterClockWise)

- drawCircle(context, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, cX, cY, r)

- drawCircle_Fill(context, fillStyle, globalAlpha, cX, cY, r)

- drawCircle_Line(context, lineWidth, strokeStyle, globalAlpha, cX, cY, r)

- drawGradient_Circular(context, cX, cY, innerRadius, outerRadius, colorStops)

- drawGradient_Linear(context, x0, y0, x1, y1, colorStops)

- drawImage(context)

- drawLine(context, lineWidth, strokeStyle, globalAlpha, sX, sY, eX, eY)

- drawLine_Gradient(context, lineWidth, globalAlpha, sX, sY, eX, eY, colorStops)

- drawPolygon(context, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, a)

- drawPolygon_Gradient_Linear(context, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, a, sX, sY, eX, eY, colorStops)

- drawPolygon_Gradient_Linear_Center(context, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, a, colorStops)

- drawPolyline(context, lineWidth, strokeStyle, globalAlpha, a)

- drawPolyline_Gradient_Linear(context, lineWidth, globalAlpha, a, sX, sY, eX, eY, colorStops)

- drawPolyline_Gradient_Linear_Center(context, lineWidth, globalAlpha, a, colorStops)

- drawRegularPolygon(context, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, cX, cY, r, sides)

- drawPolygon(context, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, points);

- drawRect(contexto, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, l, t, r, b)

- drawRect_Fill(contexto, fillStyle, globalAlpha, l, t, r, b)

- drawRect_Line(contexto, lineWidth, strokeStyle, globalAlpha, l, t, r, b)

- drawText(context, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, font, text, x, y, maxWidth)

- drawText_Fill(context, fillStyle, globalAlpha, font, text, x, y, maxWidth)

- drawText_Line(context, lineWidth, strokeStyle, globalAlpha, font, text, x, y, maxWidth)

---