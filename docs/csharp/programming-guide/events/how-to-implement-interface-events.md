---
title: "方法 : インターフェイス イベントを実装する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "イベント [C#], インターフェイス"
  - "インターフェイス [C#], イベントの実装 (クラスへの)"
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : インターフェイス イベントを実装する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[インターフェイス](../../../csharp/language-reference/keywords/interface.md)は[イベント](../../../csharp/language-reference/keywords/event.md)を宣言できます。  次の例は、クラスにインターフェイス イベントを実装する方法を示しています。  基本的な方法は、インターフェイスのメソッドやプロパティを実装する方法と同じです。  
  
### クラスにインターフェイス イベントを実装するには  
  
-   クラス内にイベントを宣言し、適切な領域で呼び出します。  
  
    ```  
    namespace ImplementInterfaceEvents  
    {  
        public interface IDrawingObject  
        {  
            event EventHandler ShapeChanged;  
        }  
        public class MyEventArgs : EventArgs   
        {  
            // class members  
        }  
        public class Shape : IDrawingObject  
        {  
            public event EventHandler ShapeChanged;  
            void ChangeShape()  
            {  
                // Do something here before the event…  
  
                OnShapeChanged(new MyEventArgs(/*arguments*/));  
  
                // or do something here after the event.   
            }  
            protected virtual void OnShapeChanged(MyEventArgs e)  
            {  
                if(ShapeChanged != null)  
                {  
                   ShapeChanged(this, e);  
                }  
            }  
        }  
  
    }  
    ```  
  
## 使用例  
 次の例では、クラスが複数のインターフェイスを継承し、各インターフェイスが同じ名前のイベントを持っているという、あまり一般的ではない状態の処理方法を示します。  この例では、1 つ以上のイベントに対する明示的なインターフェイス実装が必要です。  イベントの明示的なインターフェイス実装を記述するときは、イベント アクセサー `add` および `remove` も記述する必要があります。  通常、これらのイベント アクセサーはコンパイラによって提供されますが、この例では提供されません。  
  
 ユーザー固有のアクセサーを指定して、2 つのイベントをクラス内の単一のイベントで表すか、別々のイベントで表すかを指定できます。  たとえば、インターフェイスの仕様により、イベントを複数回発生させる必要がある場合、各イベントをクラス内の別々の実装に関連付けることができます。  次の例では、サブスクライバーで `IShape` または `IDrawingObject` の図形参照をキャストすることにより、受信する `OnDraw` イベントを確認します。  
  
 [!CODE [csProgGuideEvents#10](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEvents#10)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [明示的なインターフェイスの実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)   
 [方法 : 派生クラスから基本クラス イベントを発生させる](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)