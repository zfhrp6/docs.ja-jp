---
title: "方法: Null 許容型を識別する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "null 許容型 [C#], 識別"
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 7
---
# 方法: Null 許容型を識別する (C# プログラミング ガイド)
C\# の [typeof](../../../csharp/language-reference/keywords/typeof.md) 演算子を使用して、Null 許容型を表す <xref:System.Type> オブジェクトを作成できます。  
  
```  
System.Type type = typeof(int?);  
```  
  
 <xref:System.Reflection> 名前空間のクラスおよびメソッドを使用して、Null 許容型を表す <xref:System.Type> オブジェクトを作成することもできます。  ただし、実行時に <xref:System.Object.GetType%2A> メソッドまたは `is` 演算子を使用して Null 許容型の変数から型情報を取得しようとすると、Null 許容型ではなく基になる型を表す <xref:System.Type> オブジェクトが作成されます。  
  
 Null 許容型に対して `GetType` を呼び出すと、型が暗黙的に <xref:System.Object> に変換されるときに、ボックス化操作が実行されます。  このため、<xref:System.Object.GetType%2A> は常に、Null 許容型ではなく基になる型を表す <xref:System.Type> オブジェクトを返します。  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 C\# の [is](../../../csharp/language-reference/keywords/is.md) 演算子も Null 許容型に作用します。  このため、変数が Null 許容型であるかどうかを確認する目的で `is` を使用することはできません。  次の例の `is` 演算子は、Nullable\<int\> 変数を整数値として処理します。  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## 使用例  
 次のコードを使用して、<xref:System.Type> オブジェクトが Null 許容型を表しているかどうかを確認します。  このトピックで前述したように、`Type` オブジェクトが <xref:System.Object.GetType%2A> の呼び出しから返された場合、このコードは常に false を返します。  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## 参照  
 [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)   
 [Null 許容型のボックス化](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)