#include <stdio.h>
#define MAX_VERTICES 50
#define MAX_EDGES 50
#define NO_EDGE -1
typedef struct {
int n, m;
int A[MAX_VERTICES][MAX_EDGES];
} Graph;
void init_graph(Graph* G, int n, int m) {
int i, j;
G->n = n;
G->m = m;
for (i = 1; i <= n; i++)
for (j = 1; j <= m; j++)
G->A[i][j] = NO_EDGE;
}
void add_edge(Graph* G, int x, int y, int w) {
G->A[x][y] = w;
G->A[y][x] = w;
}
#define INFINITY 9999999
int mark[MAX_VERTICES];
int pi[MAX_VERTICES];
int p[MAX_VERTICES];
void Dijkstra(Graph* G, int s) {
int i, j, it;
for (i = 1; i <= G->n; i++) {
pi[i] = INFINITY;
mark[i] = 0;
}
pi[s] = 0;
p[s] = -1;
for (it = 1; it < G->n; it++) {
int min_pi = INFINITY;
for (j = 1; j <= G->n; j++)
if (mark[j] == 0 && pi[j] < min_pi) {
min_pi = pi[j];
i = j;
}
mark[i] = 1;
for (j = 1; j <= G->n; j++)
if (G->A[i][j] != NO_EDGE && mark[j] == 0) {
if (pi[i] + G->A[i][j] < pi[j]) {
pi[j] = pi[i] + G->A[i][j];
p[j] = i;
}
}
}
}
int main() {
// freopen("dt.txt", "r", stdin);
Graph G;
int n, m, u, v, e, w;
scanf("%d%d", &n, &m);
init_graph(&G, n, m);
for (e = 1; e <= m; e++) {
scanf("%d%d%d", &u, &v, &w);
add_edge(&G,u,v,w);
}
Dijkstra(&G, 1);
if(pi[n]>0){
printf("%d", pi[n]);
}
else printf("-1");
return 0;
}
==============================================

#include <stdio.h>
#define MAX_VERTICES 50
#define MAX_EDGES 50
#define NO_EDGE -1
typedef struct {
int n, m;
int A[MAX_VERTICES][MAX_EDGES];
} Graph;
void init_graph(Graph* G, int n, int m) {
int i, j;
G->n = n;
G->m = m;
for (i = 1; i <= n; i++)
for (j = 1; j <= m; j++)
G->A[i][j] = NO_EDGE;
}
void add_edge(Graph* G, int x, int y, int w) {
G->A[x][y] = w;
G->A[y][x] = w;
}
#define INFINITY 9999999
int mark[MAX_VERTICES];
int pi[MAX_VERTICES];
int p[MAX_VERTICES];
void Dijkstra(Graph* G, int s) {
int i, j, it;
for (i = 1; i <= G->n; i++) {
pi[i] = INFINITY;
mark[i] = 0;
}
pi[s] = 0;
p[s] = -1;
for (it = 1; it < G->n; it++) {
int min_pi = INFINITY;
for (j = 1; j <= G->n; j++)
if (mark[j] == 0 && pi[j] < min_pi) {
min_pi = pi[j];
i = j;
}
mark[i] = 1;
for (j = 1; j <= G->n; j++)
if (G->A[i][j] != NO_EDGE && mark[j] == 0) {
if (pi[i] + G->A[i][j] < pi[j]) {
pi[j] = pi[i] + G->A[i][j];
p[j] = i;
}
}
}
}
int main() {
// freopen("dt.txt", "r", stdin);
Graph G;
int n, m, u, v, e, w;
scanf("%d%d", &n, &m);
init_graph(&G, n, m);
for (e = 1; e <= m; e++) {
scanf("%d%d%d", &u, &v, &w);
add_edge(&G,u,v,w);
}
Dijkstra(&G, 1);
if(pi[n]>0){
printf("%d", pi[n]);
}
else printf("-1");
return 0;
}
