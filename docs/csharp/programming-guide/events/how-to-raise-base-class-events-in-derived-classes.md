---
title: "方法 : 派生クラスから基本クラス イベントを発生させる (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 13501f51a1e99eb6fb792a1c6abe5c7029cc020a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>方法 : 派生クラスから基本クラス イベントを発生させる (C# プログラミング ガイド)
ここでは単純な例を使用し、派生クラスからも発生させることができるように基底クラスでイベントを宣言する標準的な方法について説明します。 このパターンは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] クラス ライブラリの Windows フォーム クラスで広く使用されています。  
  
 他のクラスの基底クラスとして使用できるクラスを作成するときは、イベントは宣言元のクラス内からしか呼び出せない特別な種類のデリゲートであることを考慮する必要があります。 派生クラスは、基底クラスの中で宣言されたイベントを直接呼び出せません。 常に基底クラスからイベントを発生させるようにすると便利な場合もありますが、ほとんどの場合、派生クラスで基底クラス イベントを呼び出せるようにするべきです。 そのために、イベントをラップする基底クラスで、保護された呼び出しメソッドを作成できます。 この呼び出しメソッドを呼び出すかオーバーライドすることによって、派生クラスから間接的にイベントを呼び出すことができます。  
  
> [!NOTE]
>  基底クラスで仮想イベントを宣言したり、派生クラスでそれらをオーバーライドしたりしないでください。 C# コンパイラはこれらを正しく処理できず、派生イベントに対するサブスクライバーが基底クラスのイベントを実際に受信登録するかどうかは予測できません。  
  
## <a name="example"></a>例  
 [!code-cs[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Windows フォーム内でのイベント ハンドラーの作成](https://msdn.microsoft.com/library/dacysss4.aspx)

