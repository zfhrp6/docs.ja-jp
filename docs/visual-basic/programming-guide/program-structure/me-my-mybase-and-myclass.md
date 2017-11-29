---
title: "Visual Basic における Me、My、MyBase、MyClass"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bebf404cd65d1b3a2c4059d3a7c986f0157dfe2d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="f37d9-102">Visual Basic における Me、My、MyBase、MyClass</span><span class="sxs-lookup"><span data-stu-id="f37d9-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="f37d9-103">`Me`、 `My`、 `MyBase`、および`MyClass`で[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]似た名前が、さまざまな目的があります。</span><span class="sxs-lookup"><span data-stu-id="f37d9-103">`Me`, `My`, `MyBase`, and `MyClass` in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] have similar names, but different purposes.</span></span> <span data-ttu-id="f37d9-104">このトピックでは、これらを区別するためにこれらのエンティティの各を説明します。</span><span class="sxs-lookup"><span data-stu-id="f37d9-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="f37d9-105">Me</span><span class="sxs-lookup"><span data-stu-id="f37d9-105">Me</span></span>  
 <span data-ttu-id="f37d9-106">`Me`キーワードはクラスまたは構造体の現在のコードが実行されているは、特定のインスタンスを参照する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="f37d9-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="f37d9-107">`Me`オブジェクト変数または現在のインスタンスを参照する構造体変数のいずれかのように動作します。</span><span class="sxs-lookup"><span data-stu-id="f37d9-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="f37d9-108">使用して`Me`は別のクラス、構造体、またはモジュール内のプロシージャにクラスまたは構造体の現在実行中のインスタンスに関する情報を渡すために特に便利です。</span><span class="sxs-lookup"><span data-stu-id="f37d9-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="f37d9-109">たとえば、モジュール内に、次の手順があるとします。</span><span class="sxs-lookup"><span data-stu-id="f37d9-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="f37d9-110">このプロシージャを呼び出すしの現在のインスタンスを渡すことができます、<xref:System.Windows.Forms.Form>次のステートメントを使用して、引数としてのクラスです。</span><span class="sxs-lookup"><span data-stu-id="f37d9-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="f37d9-111">My</span><span class="sxs-lookup"><span data-stu-id="f37d9-111">My</span></span>  
 <span data-ttu-id="f37d9-112">`My`機能の数を容易かつ直観的なアクセスを提供する[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラスを有効にすると、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンピューター、アプリケーション、設定、リソースと対話するユーザー。</span><span class="sxs-lookup"><span data-stu-id="f37d9-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="f37d9-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="f37d9-113">MyBase</span></span>  
 <span data-ttu-id="f37d9-114">`MyBase`キーワードはクラスの現在のインスタンスの基本クラスを参照するオブジェクト変数のように動作します。</span><span class="sxs-lookup"><span data-stu-id="f37d9-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="f37d9-115">`MyBase`通常オーバーライドまたは派生クラスでシャドウされている基本クラスのメンバーへのアクセスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f37d9-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="f37d9-116">`MyBase.New`派生クラスのコンス トラクターから基本クラスのコンス トラクターを明示的に呼び出すに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f37d9-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="f37d9-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="f37d9-117">MyClass</span></span>  
 <span data-ttu-id="f37d9-118">`MyClass`キーワードが最初に実装されたクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。</span><span class="sxs-lookup"><span data-stu-id="f37d9-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="f37d9-119">`MyClass`ような`Me`、上のすべてのメソッド呼び出しとして扱われますはこのメソッドが、`NotOverridable`です。</span><span class="sxs-lookup"><span data-stu-id="f37d9-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f37d9-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f37d9-120">See Also</span></span>  
 [<span data-ttu-id="f37d9-121">継承の基本</span><span class="sxs-lookup"><span data-stu-id="f37d9-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
