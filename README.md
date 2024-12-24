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

# Sample source

- Example link
	- http://thdtjsdn.com:49310/app_tool/html_page/DrawCanvas/index.html

```javascript
const APIS = TAPI.w.apis.CANVASContextDraw;

const CANVAS = TAPI.ge('ID-CANVAS');
const CONTEXT = CANVAS.getContext('2d');

const COLOR_STOPS = [0.0, APIS_RANDOM_HEXCOLOR(), 0.5, APIS_RANDOM_HEXCOLOR(), 1.0, APIS_RANDOM_HEXCOLOR()];

const EVENT_LISTENERS = {
	Clear: function () { CONTEXT.clearRect(0, 0, CANVAS.width, CANVAS.height); }

	, Arc: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawArc(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getRadius_Random(), getArc_Random(), Math.PI, false
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawArc_Fill(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getRadius_Random(), getArc_Random(), Math.PI, false
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawArc_Line(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getRadius_Random(), getArc_Random(), Math.PI, false
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	, Circle: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawCircle(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getRadius_Random()
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawCircle_Fill(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getRadius_Random()
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawCircle_Line(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getRadius_Random()
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	, Rect: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawRect(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getX_Random()/8, getY_Random()/8
		);

		APIS.drawRect_Fill(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getX_Random()/8, getY_Random()/8
		);

		APIS.drawRect_Line(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getX_Random()/8, getY_Random()/8
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, Line: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawLine(CONTEXT, 5, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getX_Random(), getY_Random(), getX_Random(), getY_Random());
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	, LineGradient: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawLine_Gradient(CONTEXT, 5, 1.0, getX_Random(), getY_Random(), getX_Random(), getY_Random(), COLOR_STOPS);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, Polygon: function () {
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolygon(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), 2, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), a);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	, PolygonGradientLinear: function () {
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolygon_Gradient_Linear(CONTEXT, getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, 150, 150, 350, 250, COLOR_STOPS
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, PolygonGradientLinearCenter: function () {
		var COLOR_STOPS = [0.0, APIS_RANDOM_HEXCOLOR(), 0.5, APIS_RANDOM_HEXCOLOR(), 1.0, APIS_RANDOM_HEXCOLOR()];
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolygon_Gradient_Linear_Center(CONTEXT, getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, COLOR_STOPS
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, Polygon_Dashed_NN: function () {
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolygon_Dashed(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, Polygon_Dashed_NNN: function () {
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolygon_Dashed(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, Polygon_Dashed_NNNN: function () {
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolygon_Dashed(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random(), getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, PolygonBezierCurve: function () {
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolygonBezierCurve(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	, PolygonCurve: function () {
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolygonCurve(CONTEXT, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	//----------------------------------------------------------------------------------------------------;

	, Polyline: function () {
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolyline(CONTEXT, getLineWidth_Random(), APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), a);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, PolylineGradientLinear: function () {
		var COLOR_STOPS = [0.0, APIS_RANDOM_HEXCOLOR(), 0.5, APIS_RANDOM_HEXCOLOR(), 1.0, APIS_RANDOM_HEXCOLOR()];
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawPolyline_Gradient_Linear(CONTEXT, getLineWidth_Random(), getAlpha_Random(), a, 150, 150, 350, 250, COLOR_STOPS);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, PolylineGradientLinearCenter: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }

		var COLOR_STOPS = [0.0, APIS_RANDOM_HEXCOLOR(), 0.5, APIS_RANDOM_HEXCOLOR(), 1.0, APIS_RANDOM_HEXCOLOR()];
		APIS.drawPolyline_Gradient_Linear_Center(CONTEXT, getLineWidth_Random(), getAlpha_Random(), a, COLOR_STOPS);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, Polyline_Dashed_NN: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolyline_Dashed(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, Polyline_Dashed_NNN: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolyline_Dashed(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, Polyline_Dashed_NNNN: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolyline_Dashed(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random(), getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, PolylineBezierCurve: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolylineBezierCurve(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	, PolylineBezierCurve_Dashed_NN: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolylineBezierCurve_Dashed(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, PolylineBezierCurve_Dashed_NNN: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolylineBezierCurve_Dashed(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, PolylineBezierCurve_Dashed_NNNN: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolylineBezierCurve_Dashed(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random(), getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, PolylineCurve: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolylineCurve(CONTEXT, getLineWidth_Random
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), a
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	, PolylineCurve_Dashed_NN: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolylineCurve_Dashed(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, PolylineCurve_Dashed_NNN: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolylineCurve_Dashed(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, PolylineCurve_Dashed_NNNN: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolylineCurve_Dashed(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, [getDashed_Random(), getDashed_Random(), getDashed_Random(), getDashed_Random()]
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, PolylinePressureFront: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		var a = [];
		var i = 0, iLen = APIS_RANDOM_NUMBER(5, 10);
		for (; i < iLen; ++i) { a.push(getX_Random(), getY_Random()); }
		APIS.drawPolyline__PressureFront(CONTEXT, getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, a, 20
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, RegularPolygon: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawRegularPolygon(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getRadius_Random(), getSides_Random()
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, RegularPolygonRotation: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawRegularPolygon_Rotation(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), getLineWidth_Random()
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getRadius_Random(), getSides_Random(), getRotation_Random()
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, RegularPolygonGradientLinear: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawRegularPolygon_Gradient_Linear(CONTEXT
			, getAlpha_Random(), getLineWidth_Random(), APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getX_Random(), getY_Random(), getRadius_Random(), getSides_Random(), getRotation_Random()
			, 100, 100, 200, 200, COLOR_STOPS
		);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	, GradientCircular: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawGradient_Circular(CONTEXT, getX_Random(), getY_Random(), getRadius_Random(), getRadius_Random(), COLOR_STOPS);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	, GradientLinear: function () {
		if (TAPI.gec('ID-CHECKBOX--PATH-BEGIN')) { CONTEXT.beginPath(); }
		APIS.drawGradient_Linear(CONTEXT, getX_Random(), getY_Random(), getX_Random(), getY_Random(), COLOR_STOPS);
		if (TAPI.gec('ID-CHECKBOX--PATH-CLOSE')) { CONTEXT.closePath(); }

		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}

	//----------------------------------------------------------------------------------------------------;

	, Bitmap: function () {
		var img = new Image();
		function drawImage(bitmap) {
			APIS.drawImageBitmap(CONTEXT, bitmap, getX_Random(), getY_Random(), 100, 100); // 이미지 객체, x 좌표, y 좌표, 너비, 높이
			if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(function () { drawImage(bitmap); }); }
		}
		img.onload = function () { createImageBitmap(img).then(drawImage); };
		img.src = 'http://thdtjsdn.com:49310/app_thdtjsdn/html_page/Resume/index.photo.png'; // 사용할 이미지의 URL
	}
	, BitmapRotation: function () {
		var img = new Image();
		function drawImage(bitmap) {
			APIS.drawImageBitmap_Rotation(CONTEXT, bitmap, getX_Random(), getY_Random(), 100, 100, getRotation_Random()); // 비트맵 객체, x 좌표, y 좌표, 너비, 높이, 45도 회전
			if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(function () { drawImage(bitmap); }); }
		}
		img.onload = function () { createImageBitmap(img).then(drawImage); };
		img.src = 'http://thdtjsdn.com:49310/app_thdtjsdn/html_page/Resume/index.photo.png'; // 사용할 이미지의 URL
	}

	, Image: function () {
		var img = new Image();
		function drawImage() {
			APIS.drawImage(CONTEXT, img, getX_Random(), getY_Random(), 100, 100); // 이미지 객체, x 좌표, y 좌표, 너비, 높이
			if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
		}
		img.onload = function () { drawImage() };
		img.src = 'http://thdtjsdn.com:49310/app_thdtjsdn/html_page/Resume/index.photo.png'; // 사용할 이미지의 URL
	}
	, ImageRotation: function () {
		var img = new Image();
		function drawImage() {
			APIS.drawImage_Rotation(CONTEXT, img, getX_Random(), getY_Random(), 100, 100, getRotation_Random()); // 이미지 객체, x 좌표, y 좌표, 너비, 높이, 45도 회전
			if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
		}
		img.onload = function () { drawImage(); };
		img.src = 'http://thdtjsdn.com:49310/app_thdtjsdn/html_page/Resume/index.photo.png'; // 사용할 이미지의 URL
	}

	//----------------------------------------------------------------------------------------------------;

	, Text: function () {
		APIS.drawText(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), 2
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getFontSize_Random() + 'px Arial', 'THDTJSDN'
			, getX_Random(), getY_Random(), 500
		);
		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, TextRotation: function () {
		APIS.drawText_Rotation(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random(), 2
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getFontSize_Random() + 'px Arial', 'THDTJSDN'
			, getX_Random(), getY_Random(), 500, getRotation_Random()
		);
		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, TextFill: function () {
		APIS.drawText_Fill(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getFontSize_Random() + 'px Arial', 'THDTJSDN'
			, getX_Random(), getY_Random(), 500
		);
		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, TextFillRotation: function () {
		APIS.drawText_Fill_Rotation(CONTEXT
			, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getFontSize_Random() + 'px Arial', 'THDTJSDN'
			, getX_Random(), getY_Random(), 500
			, getRotation_Random()
		);
		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, TextLine: function () {
		APIS.drawText_Line_Rotation(CONTEXT
			, 2, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getFontSize_Random() + 'px Arial', 'THDTJSDN'
			, getX_Random(), getY_Random(), 500
			, getRotation_Random()
		);
		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
	}
	, drawTextLineRotation: function () {
		APIS.drawText_Line_Rotation(CONTEXT
			, 2, APIS_RANDOM_HEXCOLOR(), getAlpha_Random()
			, getFontSize_Random() + 'px Arial', 'THDTJSDN'
			, getX_Random(), getY_Random(), 500
			, getRotation_Random()
		);
		if (TAPI.gec('ID-CHECKBOX--CONTINUE-CREATE')) { requestAnimationFrame(arguments.callee); }
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

- drawImage(context, img, dx, dy, dw, dh)
- drawImage_Rotation(context, img, dx, dy, dw, dh, rotation)
- drawImageBitmap(context, bitmap, dx, dy, dw, dh)
- drawImageBitmap_Rotation(context, bitmap, dx, dy, dw, dh, rotation)

- drawLine(context, lineWidth, strokeStyle, globalAlpha, sX, sY, eX, eY)
- drawLine_Gradient(context, lineWidth, globalAlpha, sX, sY, eX, eY, colorStops)

- drawPolygon(context, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, a)
- drawPolygon_Gradient_Linear(context, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, a, sX, sY, eX, eY, colorStops)
- drawPolygon_Gradient_Linear_Center(context, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, a, colorStops)

- drawPolyline(context, lineWidth, strokeStyle, globalAlpha, a)
- drawPolyline_Gradient_Linear(context, lineWidth, globalAlpha, a, sX, sY, eX, eY, colorStops)
- drawPolyline_Gradient_Linear_Center(context, lineWidth, globalAlpha, a, colorStops)

- drawRegularPolygon(context, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, cX, cY, r, sides)
- drawRegularPolygon_Gradient_Linear(context, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, cX, cY, r, sides, rotation, sX, sY, eX, eY, colorStops) {

- drawRect(contexto, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, l, t, r, b)
- drawRect_Fill(contexto, fillStyle, globalAlpha, l, t, r, b)
- drawRect_Line(contexto, lineWidth, strokeStyle, globalAlpha, l, t, r, b)

- drawText(context, fillStyle, globalAlpha_Fill, lineWidth, strokeStyle, globalAlpha_Line, font, text, x, y, maxWidth)
- drawText_Fill(context, fillStyle, globalAlpha, font, text, x, y, maxWidth)
- drawText_Line(context, lineWidth, strokeStyle, globalAlpha, font, text, x, y, maxWidth)

---