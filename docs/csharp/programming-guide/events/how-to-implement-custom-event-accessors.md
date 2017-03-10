---
title: "方法 : カスタム イベント アクセサーを実装する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "アクセサー [C#], イベント アクセサー"
  - "add アクセサー [C#]"
  - "イベント [C#], add アクセサー"
  - "イベント [C#], remove アクセサー"
  - "remove アクセサー [C#]"
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 7
---
# 方法 : カスタム イベント アクセサーを実装する (C# プログラミング ガイド)
イベントは、宣言元のクラス内でしか呼び出せない特殊なマルチキャスト デリゲートです。  クライアント コードは、イベント発生時に呼び出されるメソッドへの参照を提供することにより、イベントにサブスクライブします。  それらのメソッドは、イベント アクセサーを使用してデリゲートの呼び出しリストに追加されます。イベント アクセサーはプロパティ アクセサーに似ていますが、イベント アクセサーには `add` および `remove` という名前が付いている点が異なります。  ほとんどの場合、カスタム イベント アクセサーを指定する必要はありません。  コードでカスタム イベント アクセサーを指定していない場合は、コンパイラによって自動的に追加されます。  ただし、カスタム動作を指定することが必要な場合もあります。  「[方法 : インターフェイス イベントを実装する](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)」のトピックでは、そのような場合の一例を示しています。  
  
## 使用例  
 次の例は、カスタム イベント アクセサー add および remove を実装する方法を示しています。  アクセサー内部のコードは任意のコードに置き換えることができますが、新しいイベント ハンドラー メソッドを追加または削除する前に、イベントをロックすることをお勧めします。  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
  
```  
  
## 参照  
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)