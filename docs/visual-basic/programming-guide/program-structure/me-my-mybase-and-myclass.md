---
title: "Me、My、MyBase、および Visual Basic で MyClass |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
dev_langs:
- VB
helpviewer_keywords:
- My object
- self-reference, Me keyword
- MyClass keyword, relationship to similar programming elements
- Me keyword, relationship to similar programming elements
- Me keyword, referring to the current instance of an object
- Me keyword
- self-reference
- current instance, Me keyword
- MyBase keyword, relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3ba634eb28c25f47a0e88c856b916383b6ad15a2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="8f7a7-102">Visual Basic における Me、My、MyBase、MyClass</span><span class="sxs-lookup"><span data-stu-id="8f7a7-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="8f7a7-103">`Me`、 `My`、 `MyBase`、および`MyClass`で[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]類似した名前が、さまざまな目的があります。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-103">`Me`, `My`, `MyBase`, and `MyClass` in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] have similar names, but different purposes.</span></span> <span data-ttu-id="8f7a7-104">このトピックでは、それらを区別するために各エンティティを説明します。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="8f7a7-105">Me</span><span class="sxs-lookup"><span data-stu-id="8f7a7-105">Me</span></span>  
 <span data-ttu-id="8f7a7-106">`Me`キーワードは、クラスまたは構造体の現在のコードが実行されているは、特定のインスタンスを参照する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="8f7a7-107">`Me`オブジェクト変数または現在のインスタンスを参照する構造体変数のいずれかのように動作します。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="8f7a7-108">使用して`Me`クラスまたは構造体の現在実行中のインスタンスに関する情報を別のクラス、構造体、またはモジュール内のプロシージャに渡すにとって特に便利です。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="8f7a7-109">たとえば、モジュールに、次の手順があるとします。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="8f7a7-110">このプロシージャを呼び出すし、現在のインスタンスを渡すことができます、<xref:System.Windows.Forms.Form>クラスを次のステートメントを使用して、引数として</xref:System.Windows.Forms.Form>。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="8f7a7-111">My</span><span class="sxs-lookup"><span data-stu-id="8f7a7-111">My</span></span>  
 <span data-ttu-id="8f7a7-112">`My`機能の数を簡単かつ直感的なアクセスを提供する[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]クラスを有効にすると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンピューター、アプリケーション、設定、リソースと対話します。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes, enabling the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="8f7a7-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="8f7a7-113">MyBase</span></span>  
 <span data-ttu-id="8f7a7-114">`MyBase`キーワードはクラスの現在のインスタンスの基底クラスへの参照オブジェクト変数のように動作します。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="8f7a7-115">`MyBase`オーバーライドまたは派生クラスでシャドウされている基本クラスのメンバーにアクセスするよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="8f7a7-116">`MyBase.New`派生クラスのコンス トラクターから基本クラス コンス トラクターを明示的に呼び出すに使用されます。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="8f7a7-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="8f7a7-117">MyClass</span></span>  
 <span data-ttu-id="8f7a7-118">`MyClass`キーワードが最初に実装されているクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="8f7a7-119">`MyClass`ような`Me`、それに対するすべてのメソッド呼び出しとして扱われますはこのメソッドが、`NotOverridable`です。</span><span class="sxs-lookup"><span data-stu-id="8f7a7-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f7a7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f7a7-120">See Also</span></span>  
 [<span data-ttu-id="8f7a7-121">継承の基本</span><span class="sxs-lookup"><span data-stu-id="8f7a7-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
