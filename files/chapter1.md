### 第一章 代码无错就是优 －－－简单工厂模式

1.简单工厂模式
```php
<?php 

class Operation
{
    protected  $a = 0;
    protected  $b = 0;

    public function setA($a)
    {
        $this->a = $a;
    }

    public function setB($b)
    {
        $this->b = $b;
    }

    public function getResult()
    {
        $result = 0;
        return $result;
    }
}

/**
*  add 
*/
class OperationAdd extends Operation
{
    public function getResult()
    {
        return $this->a + $this->b;
    }
}

/**
* Mul
*/
class OperationMul extends Operation
{
    public function getResult()
    {
        return $this->a * $this->b;
    } 
}

/**
* sub
*/
class OperationSub extends Operation
{
    public function getResult()
    {
        return $this->a - $this->b;
    }
}

/**
* div
*/
class OperationDiv extends Operation
{
    public function getResult()
    {
        return $this->a / $this->b;
    }
}


/**
* operation factory
*/
class OperationFactory
{
    public static function createOperation($operation)
    {
        switch ($operation) {
            case '+':
                $oper = new OperationAdd();
                break;
            case '-':
                $oper = new OperationSub();
                break;
            case '/':
                $oper = new OperationDiv();
                break;
            case '*':
                $oper = new OperationMul();
                break;
        }
        return $oper;
    }
}
// 客户端代码
$operation = OperationFactory::createOperation('+');
$operation->setA(1);
$operation->seB(2);
echo $operation->getResult()."\n";
```



总结

> 学会通过分封装，继承，多态把程序的藕合度降低

> 复用，不是复制！

> 高内聚，低耦合

下一章：[第二章 商场促销 －－－ 策略模式](https://github.com/flyingalex/design-patterns-by-php/blob/master/files/chapter2.md)
