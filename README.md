#include <stdio.h>
#include <stdlib.h>

#define struct(n) typedef struct n n; struct n
#define new(t) (malloc(sizeof(t)))


struct(node2) {
  int data;
  node2 * one, * two;
};
struct listnode {
  int data; struct listnode * next;
};

 struct listnode * preorderwalk(node2 * ht) {
   struct listnode ** m;

  if (ht == NULL) return NULL;
  //addtolist(hs,ht->data);
  for (node2 *p = ht->one; p != NULL; p = p->two){
      struct listnode * p1 = malloc(sizeof(struct listnode));
    *p1 = (struct listnode){p->data,*m};
    *m = p1;
  }
    return m;
    //* n = preorderwalk(p);
}

void printlist(struct listnode * n) {
  for (; n != NULL; n = n->next)
    printf("%d ",n->data);
  putchar('\n');
}

void addtolist(node2 * h, int number) {

  if (h == NULL) return NULL;
  //addtolist(hs,ht->data);
  for (node2 *p = h->one; (p+1) != NULL; p = p->two){
                              if(number < p->data){

                             node2 *next = new(node2);
                             node2 *prim = new(node2);
                             prim = p->one;
                             p = next->one;
                             next = prim->one;
                             p->data = number;
                              }
     if(p->data > (p++)->data){
               int temp = p->data;
               p->data = (p++)->data;
               (p++)->data = temp;
     }

          if(p->data > p->two){
               int temp = p->data;
               p->data = p->two;
               p->data = temp;
     }
  }
}
int main() {
  //char *s = "abcdefghij";
  struct listnode * head = NULL;

  node2 *a = new(node2); *a = (node2){0,NULL,NULL};
  node2 *b = new(node2); *b = (node2){1,NULL,NULL};
  node2 *c = new(node2); *c = (node2){2,NULL,NULL};
  node2 *d = new(node2); *d = (node2){3,NULL,NULL};
  node2 *e = new(node2); *e = (node2){4,NULL,NULL};
  node2 *f = new(node2); *f = (node2){5,NULL,NULL};
  node2 *g = new(node2); *g = (node2){6,NULL,NULL};
  node2 *h = new(node2); *h = (node2){7,NULL,NULL};
  node2 *i = new(node2); *i = (node2){8,NULL,NULL};
  node2 *j = new(node2); *j = (node2){9,NULL,NULL};
  a->one = b;
  b->one = e;
  b->two = c;    // РџРѕСЃС‚СЂРѕСЏРІР°РјРµ РґСЉСЂРІРѕ РєР°С‚Рѕ РЅР° СЃС…РµРјР°С‚Р°:
  c->two = d;    //        a
  d->one = g;    //   b    c    d
  e->two = f;    // e   f     g h i
  f->one = j;    //     j
  g->two = h;
  h->two = i;
   head = preorderwalk(a);
   printlist(head);
   int num = 5;
   addtolist(a, num);
  node2 * p = NULL; //preorderwalk(a); printlist(p);
  node2 * q = NULL; //postorderwalk(a,&q); printlist(q);
}
