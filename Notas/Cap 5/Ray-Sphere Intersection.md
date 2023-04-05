Dada a equação da esfera normal de centro (0,0,0), um ponto **P=(x,y,z)** está na esfera se:
$$x² + y² + z² = r²$$
r é o raio da esfera.
E caso a esfera tenha centro **(Cx, Cy, Cz)**:
$$
(x - Cx)² + (y - Cy)² + (z - Cz)² = r²
$$

Como a reta **PC=P-C=(x-Cx, y-Cy, z-Cz)**, $PC.PC = (x-Cx)² + (y-Cy)² + (z-Cz)²$, reescrevendo a equação anterior em termos de vetores temos:
$$
PC.PC = r²
$$
ou
$$
(P - C).(P - C) = r^2
$$

>[!info]
>Usar equações em termos de vetores é útil para ligar com gráficos porquê podemos abstrair os componentes dos vetores e trabalhar diretamente com a classe (nesse caso com a classe *vec3*)

Nesse caso, queremos saber se **o raio que emitimos atingiu a esfera**, sendo o raio $P(x) = A + tB$ ([[Rays]]), podemos expandir a equação anterior para:
$$
(A+tB - C).(A+tB - C) = r²
$$
Colocando todos os termos do lado esquerdo:
$$
t^2b*b+2tb*(A-C)+(A-C)*(A-C)-r^2 = 0
$$
Isso resulta numa equação de 2º grau, que podemos resolver usando a **fórmula resolvente** e então teremos 3 casos:
- Caso **não existam raízes reais** o raio não atingiu a esfera
- Caso exista **somente 1 raiz real**, o raio atingiu 1 ponto na esfera (tangente)
- Caso existam **2 raízes reais** o raio atingiu a esfera de um lado e passou pelo outro

## Implementação
```cpp
double hit_sphere(const point3& center, double radius, const ray& r) {
	// t²b * b + 2tb*(A - C) + (A - C)*(A - C) - r² > 0
	vec3 oc = r.origin() - center;
	auto a = r.direction().length_squared();
	auto half_b = dot(oc, r.direction());
	auto c = oc.length_squared() - radius*radius;  
	
	auto discriminant = half_b*half_b - a*c;  
	
	double root;
	if (discriminant < 0) {
		root = -1.0;
	} else {
		root = (-half_b - sqrt(discriminant)) / (2.0*a);
	}
	
	return root;
}

  

color ray_color(const ray& r) {
	auto t = hit_sphere(point3(0,0,-1), 0.5, r);
	if (t > 0.0){
		vec3 N = unit_vector(r.at(t) - vec3(0,0,-1));
		return 0.5*color(N.x()+1, N.y()+1, N.z()+1);
	}
```