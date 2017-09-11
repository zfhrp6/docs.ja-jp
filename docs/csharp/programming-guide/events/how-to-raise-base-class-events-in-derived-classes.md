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
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="cdfb8-102">方法 : 派生クラスから基本クラス イベントを発生させる (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="cdfb8-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="cdfb8-103">ここでは単純な例を使用し、派生クラスからも発生させることができるように基底クラスでイベントを宣言する標準的な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="cdfb8-104">このパターンは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] クラス ライブラリの Windows フォーム クラスで広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-104">This pattern is used extensively in Windows Forms classes in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library.</span></span>  
  
 <span data-ttu-id="cdfb8-105">他のクラスの基底クラスとして使用できるクラスを作成するときは、イベントは宣言元のクラス内からしか呼び出せない特別な種類のデリゲートであることを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="cdfb8-106">派生クラスは、基底クラスの中で宣言されたイベントを直接呼び出せません。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="cdfb8-107">常に基底クラスからイベントを発生させるようにすると便利な場合もありますが、ほとんどの場合、派生クラスで基底クラス イベントを呼び出せるようにするべきです。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="cdfb8-108">そのために、イベントをラップする基底クラスで、保護された呼び出しメソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="cdfb8-109">この呼び出しメソッドを呼び出すかオーバーライドすることによって、派生クラスから間接的にイベントを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdfb8-110">基底クラスで仮想イベントを宣言したり、派生クラスでそれらをオーバーライドしたりしないでください。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="cdfb8-111">C# コンパイラはこれらを正しく処理できず、派生イベントに対するサブスクライバーが基底クラスのイベントを実際に受信登録するかどうかは予測できません。</span><span class="sxs-lookup"><span data-stu-id="cdfb8-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdfb8-112">例</span><span class="sxs-lookup"><span data-stu-id="cdfb8-112">Example</span></span>  
 <span data-ttu-id="cdfb8-113">[!code-cs[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cdfb8-113">[!code-cs[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdfb8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdfb8-114">See Also</span></span>  
 <span data-ttu-id="cdfb8-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cdfb8-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cdfb8-116">[イベント](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="cdfb8-116">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="cdfb8-117">[デリゲート](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="cdfb8-117">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="cdfb8-118">[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="cdfb8-118">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 [<span data-ttu-id="cdfb8-119">Windows フォーム内でのイベント ハンドラーの作成</span><span class="sxs-lookup"><span data-stu-id="cdfb8-119">Creating Event Handlers in Windows Forms</span></span>](https://msdn.microsoft.com/library/dacysss4.aspx)

