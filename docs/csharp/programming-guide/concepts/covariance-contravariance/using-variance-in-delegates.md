---
title: "デリゲートの分散の使用 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb8512945fa7aefa9afce4f4f1f8e0200dc3e2b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-c"></a>デリゲートの分散の使用 (C#)
メソッドをデリゲートに割り当てると、"*共変性*" と "*反変性*" により、デリゲート型をメソッドのシグネチャに柔軟に一致させることができます。 共変性により、メソッドの戻り値の型の派生を、デリゲートに定義されている型よりも強くできます。 また、反変性により、メソッドのパラメーター型の派生をデリゲート型よりも弱くできます。  
  
## <a name="example-1-covariance"></a>例 1: 共変性  
  
### <a name="description"></a>説明  
 この例は、デリゲート シグネチャ内の戻り値の型から派生した戻り値の型を持つメソッドで、デリゲートをどのように使用できるかを示しています。 `DogsHandler` が返すデータ型は `Dogs` です。これは、デリゲートに定義された `Mammals` 型の派生型です。  
  
### <a name="code"></a>コード  
  
```csharp  
class Mammals{}  
class Dogs : Mammals{}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a>例 2: 反変性  
  
### <a name="description"></a>説明  
 この例は、パラメーターの型がデリゲート シグネチャ パラメーター型の基本データ型であるメソッドで、デリゲートをどのように使用できるかを示しています。 反変性により、複数のハンドラーの代わりに単一のイベント ハンドラーを使用できます。 たとえば、`EventArgs` 入力パラメーターを受け取るイベント ハンドラーを作成し、そのイベント ハンドラーを、`MouseEventArgs` 型をパラメーターとして送信する `Button.MouseClick` イベントや `KeyEventArgs` パラメーターを送信する `TextBox.KeyDown` イベントで使用できます。  
  
### <a name="code"></a>コード  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [デリゲートの分散 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [Func および Action 汎用デリゲートでの分散の使用 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
