#include <iostream>
#include <string>
#include "vector"

using namespace std;

class Vivod {
public:
    virtual void PRINT() {

    }
    //
};

class Ingredients {
public:
int cost{0};
};

class Pepperoni : public Ingredients {
private:
    int cost{10};
public:
    Pepperoni() {}

    int getCost() const {
        return cost;
    }
};

class Cheese : public Ingredients {
private:
    int cost{20};
public:
    Cheese() {}

    int getCost() const {
        return cost;
    }
};

class Chicken : public Ingredients {
private:
    int cost{30};
public:
    Chicken() {}

    int getCost() const {
        return cost;
    }
};

class Pineapple : public Ingredients { //кошмар!
private:
    int cost{15};
public:
    Pineapple() {}

    int getCost() const {
        return cost;
    }
};

class Pear : public Ingredients {
private:
    int cost{8};
public:
    Pear() {}

    int getCost() const {
        return cost;
    }
};

class Pizza : public Vivod {
public:
    string name;
    string description;
    int cheese = 0;
    int salt = 0;
    float price = 1;
    int diameter = 1;
    vector<Ingredients> ingredients;

    const string &getName() const {
        return name;
    }

    Pizza(const string &name, const string &description, int cheese, int salt, float price, int diameter,
          const vector<Ingredients> &ingredients) : name(name), description(description), cheese(cheese), salt(salt),
                                                    price(price), diameter(diameter), ingredients(ingredients) {}

    void setName(const string &name) {
        Pizza::name = name;
    }

    const string &getDescription() const {
        return description;
    }

    void setDescription(const string &description) {
        Pizza::description = description;
    }

    int getCheese() const {
        return cheese;
    }

    void setCheese(int cheese) {
        Pizza::cheese = cheese;
    }

    int getSalt() const {
        return salt;
    }

    void setSalt(int salt) {
        Pizza::salt = salt;
    }

    float getPrice() const {
        return price;
    }

    void setPrice(float price) {
        Pizza::price = price;
    }

    int getDiameter() const {
        return diameter;
    }

    void setDiameter(int diameter) {
        Pizza::diameter = diameter;
    }

    void MoreChesee(Pizza& p) {
        cout << "How much cheese to add?\n";
        int b;
        cin >> b;
        p.setCheese(b);
        //пусть отрицательное не вводят :(
    }

    void MoreSalt(Pizza& p) {
        cout << "How much salt to add?\n";
        int b;
        cin >> b;
        p.setSalt(b);
        //тут тоже!!!
    }
    float CheckSize(Pizza p) {
        int b;
        cin >> b;
        p.setDiameter(b);
        b = p.getDiameter();
        switch (b) {
           case 1: {
               float a = p.getPrice();
               a = a * 1;
               return a;
               break;
           }
           case 2: {
               float a = p.getPrice();
               a = a * 1.25;
               return a;
               break;
           }
           case 3: {
               float a = p.getPrice();
               a = a * 1.5;
               return a;
               break;
           }
           case 4: {
               float a = p.getPrice();
               a = a * 1.75;
               return a;
               break;
           }
            default: {
                cout<<"Wrong size!!!"<<endl;
                cout<<"You will be punished, here's the largest pizza";
                float a = p.getPrice();
                a = a * 1.75;
                return a;
            }

        }
    }
    float sumPrice(Pizza p) {
        //CheckSize(*this);
        float Sum1 = this->getPrice() + this->getCheese() + this->getSalt();
        return Sum1;
    }

    void PRINT() override {
        //cout<<"Here's your pizza:"<<endl;
        cout<<"------------------"<<endl;
        cout<<this->getName()<<endl;
        cout<< this->getDescription()<<endl;
        cout<<this->getCheese()<<endl;
        cout<<this->getSalt()<<endl;
        cout<<this->getDiameter()<<endl;
        cout<<this->getPrice()<<endl;
    }
};


void MenuofPizzas() {
        cout<<"1. Pepperoni"<<endl;
        cout<<"2. Cheesy chick"<<endl;
        cout<<"3. Hawaiian"<<endl;
        cout<<"4. Sweet Pear"<<endl;
};
Pizza ChoosePizza(vector<Pizza> o) {
    int a;
    cin >> a;
    switch (a) {
        case 1: {
            Pepperoni pep;
            Cheese cheese;
            vector<Ingredients> p1 = {pep, cheese};
            Pizza PEPPERONI("Pepperoni", "Delicious pizza with spicy and tasty flavour", 0, 0, 200, 1, p1);
            return PEPPERONI;
            break;
        }
        case 2: {
            Chicken chicken;
            Cheese cheese;
            vector<Ingredients> p2 = {chicken, cheese};
            Pizza CHICKEN("Cheesy chick", "Soft chicken with hot cheese", 0, 0, 250, 1, p2);
            return CHICKEN;
            break;
        }
        case 3: {
            Chicken chicken;
            Pineapple pineapple;
            Cheese cheese;
            vector<Ingredients> p3 = {chicken, pineapple, cheese};
            Pizza PINEAPPLE("Hawaiian", "OMG, that's a pizza with pineapples and chicken", 0, 0, 260, 1, p3);
            return PINEAPPLE;
            break;
        }
        case 4: {
            Pear pear;
            Cheese cheese;
            vector <Ingredients> p4 = {pear, cheese};
            Pizza PEAR("Sweet Pear", "Delicious and sweet pizza with hot baked pears and hot cheese", 0, 0, 210, 1, p4);
            return PEAR;
            break;
        }
        default: {
            cout << "Wrong number!!!"<<endl;
            cout << "You will be punished!!!"<<endl;
            Chicken chicken;
            Pineapple pineapple;
            Cheese cheese;
            vector<Ingredients> p3 = {chicken, pineapple, cheese};
            Pizza PINEAPPLE("Hawaiian", "OMG, that's a pizza with pineapples and chicken", 0, 0, 260, 1, p3);
            return PINEAPPLE;
            break;
        }
    }
}
void Menu() {
    vector<Pizza> Order;
    float SUMPRICE = 0;
    cout<<"Hello! How can we help you\n";
    while (true) {
        cout << "What would you like to do?" << endl;
        cout << "1. Add pizza" << endl;
        cout << "2. Print Order" << endl;
        int user;
        cin >> user;
        switch (user) {
            case 1 : {
                MenuofPizzas();
                Pizza NewPizza = ChoosePizza(Order);
                cout << "Would you like to add more cheese?\n";
                NewPizza.MoreChesee(NewPizza);
                cout << "Would you like to add more salt?" << endl;
                NewPizza.MoreSalt(NewPizza);
                cout << "What size would you like for your pizza?" << endl;
                cout << "1. 25 " << endl;
                cout << "2. 30 " << endl;
                cout << "3. 35 " << endl;
                cout << "4. 40 " << endl;
                float B = NewPizza.CheckSize(NewPizza);
                NewPizza.setPrice(B);
                Order.push_back(NewPizza);
                cout << "Your current order: " << endl;
                for (Pizza& pizza : Order) {
                    pizza.PRINT();
                }
                float ORDERPRICE = NewPizza.sumPrice(NewPizza);
                //cout << "Pizza Price: " << ORDERPRICE << endl;
                SUMPRICE +=ORDERPRICE;
                cout << "------------------" << endl;
                cout << "Sum Price: " << SUMPRICE << endl;
                cout << "------------------" << endl;
                cout << "Anything else?" << endl;
                cout << "1. No." << endl;
                cout << "(Any number) Yes!" << endl;
                int y;
                cin >> y;
                if (y == 1) {
                    break;
                }
            }
            case 2: {
             if (Order.empty()) {
                 cout << "Your order is empty. :(" << endl;
             } else {
                 cout << "Your current order: " << endl;
                 for (Pizza& pizza : Order) {
                     pizza.PRINT();
                 }
             }
            }
        }
        cout << "End order?" << endl;
        cout << "1. Yes." << endl;
        cout << "(Any number) No!" << endl;
        int y;
        cin >> y;
        if (y == 1) {
            break;
        }
    }
}

int main() {
    //Pepperoni pep;
    //Cheese cheese;
    //Pineapple pineapple;
    //Chicken chicken;
    //Pear pear;
    //vector<Ingredients> p1 = {pep, cheese};
    //vector<Ingredients> p2 = {chicken, cheese};
    //vector<Ingredients> p3 = {chicken, pineapple, cheese};
    //vector <Ingredients> p4 = {pear, cheese};
    //Pizza PEPPERONI("Pepperoni", "Delicious pizza with spicy and tasty flavour", 0, 0, 200, 1, p1);
    //Pizza CHICKEN("Cheesy chick", "Soft chicken with hot cheese", 0, 0, 250, 1, p2);
    //Pizza PINEAPPLE("Hawaiian", "OMG, that's a pizza with pineapples and chicken", 0, 0, 260, 1, p3);
    //Pizza PEAR("Sweet Pear", "Delicious and sweet pizza with hot baked pears and hot cheese", 0, 0, 210, 1, p4);
    Menu();

    return 0;
}
