#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *left, *right;
};

struct node* create(int x) {
    struct node* t = (struct node*)malloc(sizeof(struct node));
    t->data = x;
    t->left = t->right = NULL;
    return t;
}

void levelOrder(struct node* root) {
    struct node* q[10];
    int front = 0, rear = 0;
    q[rear++] = root;

    while (front < rear) {
        struct node* temp = q[front++];
        printf("%d ", temp->data);
        if (temp->left) q[rear++] = temp->left;
        if (temp->right) q[rear++] = temp->right;
    }
}

int main() {
    struct node* root = create(1);
    root->left = create(2);
    root->right = create(3);
    levelOrder(root);
    return 0;
}
