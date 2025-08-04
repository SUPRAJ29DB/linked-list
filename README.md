# linked-list
```
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *createnode(int data) {
    struct node *temp = (struct node*) malloc(sizeof(struct node));
    if (!temp) {
        printf("Memory allocation error\n");
        exit(1);
    }
    temp->data = data;
    temp->next = NULL;
    return temp;
}

void insertend(int data, struct node **head) {
    struct node *newnode = createnode(data);
    if (*head == NULL) {
        *head = newnode;
    } else {
        struct node *temp = *head;
        while (temp->next != NULL) {
            temp = temp->next;
        }
        temp->next = newnode;
    }
}

void insertatbeginning(int data, struct node **head) {
    struct node *newnode = createnode(data);
    newnode->next = *head;
    *head = newnode;
}

void display(struct node *head) {
    struct node *temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

int main() {
    struct node *head = NULL;

    insertend(1, &head);
    insertend(2, &head);
    insertend(3, &head);
    insertend(4, &head);
    insertend(5, &head);
    
    printf("Linked list after insertions at end:\n");
    display(head);

    insertatbeginning(0, &head);
    insertatbeginning(-1, &head);

    printf("Linked list after insertions at beginning:\n");
    display(head);

    return 0;
}

```
