# Stragegy

## 场景举例

枚举类型支持不同方法，if...else / switch...case
```C++
enum TaxBase {
    CN_Tax,
    US_Tax,
    DE_Tax,
    FR_Tex // 更改
};

Class SalesOrder {
    TaxBase tax;
public:
    double CalculateTax() {
        //...
        if (tax == CN_Tax) {
            //CN***
        } else if (tax == US_Tax) {
            //US***
        } else if (tax == DE_Tax) {
            //DE***
        } else if (tax == FR_Tax) {
            // 更改
        }

        //......
    }
};

```

违背了开闭原则：对扩展开放对更改封闭

带来了很大的复用性负担！！！