---
title: "方法 : カスタム イベント アクセサーを実装する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ff5fedeeaa427bb62991f9b406c167647dc376d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>方法 : カスタム イベント アクセサーを実装する (C# プログラミング ガイド)
イベントは、宣言元のクラス内でしか呼び出せない特殊なマルチキャスト デリゲートです。 クライアント コードは、イベント発生時に呼び出されるメソッドへの参照を提供することにより、イベントにサブスクライブします。 これらのメソッドは、イベント アクセサーを使用してデリゲートの呼び出しリストに追加されます。イベント アクセサーはプロパティ アクセサーに似ていますが、イベント アクセサーには `add` および `remove` という名前が付いている点が異なります。 ほとんどの場合、カスタム イベント アクセサーを指定する必要はありません。 コードでカスタム イベント アクセサーを指定していない場合は、コンパイラによって自動的に追加されます。 ただし、カスタム動作の指定が必要な場合もあります。 「[方法 : インターフェイス イベントを実装する](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)」のトピックでは、そのような場合の一例を示しています。  
  
## <a name="example"></a>例  
 次の例は、カスタム イベント アクセサーの add と remove を実装する方法を示しています。 アクセサー内で任意のコードに置き換えることができますが、新しいイベント ハンドラー メソッドを追加または削除する前に、イベントをロックすることをお勧めします。  
  
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
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../csharp/programming-guide/events/index.md)  
 [event](../../../csharp/language-reference/keywords/event.md)
