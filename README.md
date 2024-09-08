# PRODUCT-SAVINGS-CALCULATOR
#include <stdio.h>

#define MAX_PRODUCTS 10

typedef struct {
    char name[50];
    float price;
    float saved;
} Product;

Product products[MAX_PRODUCTS];
int NumProducts = 0;

void addProduct() {
    if (NumProducts < MAX_PRODUCTS) {
        printf("Enter product name: ");
        scanf("%49s", products[NumProducts].name);
        printf("Enter product price: ");
        scanf("%f", &products[NumProducts].price);
        products[NumProducts].saved = 0.0;
        NumProducts++;
        printf("Product added successfully!\n");
    } else {
        printf("Maximum Number of products reached.\n");
    }
}

void displayProducts() {
    int i;
    printf("Your products:\n");
    for (i = 0; i < NumProducts; i++) {
        printf("%d. %s - Price: %.2f, Saved: %.2f, Left: %.2f\n",
               i + 1, products[i].name, products[i].price, products[i].saved,
               products[i].price - products[i].saved);
    }
}

void updateSaved() {
    int i;
    printf("Enter the product Number to update saved amount: ");
    scanf("%d", &i);
    i--; // adjust for 0-based indexing
    if (i >= 0 && i < NumProducts) {
        printf("Enter the amount saved for %s: ", products[i].name);
        scanf("%f", &products[i].saved);
        printf("Saved amount updated successfully!\n");
    } else {
        printf("Invalid product Number.\n");
    }
}

int main() {
    int choice;
    while (1) {
        printf("1. Add product\n");
        printf("2. Display products\n");
        printf("3. Update saved amount\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                addProduct();
                break;
            case 2:
                displayProducts();
                break;
            case 3:
                updateSaved();
                break;
            case 4:
                return 0;
            default:
                printf("Invalid choice.\n");
        }
    }
    return 0;
}
