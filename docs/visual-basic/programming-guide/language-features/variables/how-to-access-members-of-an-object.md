---
title: "方法: オブジェクトのメンバーにアクセスする (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 85fa4932b449bf7b9ecb3902fc17fd954ea8cfac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="4ff1d-102">方法: オブジェクトのメンバーにアクセスする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ff1d-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="4ff1d-103">オブジェクトを参照するオブジェクト変数がある場合は、多くの場合、メソッド、プロパティ、フィールド、イベントなど、そのオブジェクトのメンバーを操作します。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="4ff1d-104">たとえば、作成すると、新しい<xref:System.Windows.Forms.Form>オブジェクトを設定することができます、<xref:System.Windows.Forms.Control.Text%2A>プロパティまたは呼び出しの<xref:System.Windows.Forms.Control.Focus%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="4ff1d-105">メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="4ff1d-105">Accessing Members</span></span>  
 <span data-ttu-id="4ff1d-106">オブジェクトのメンバーは、それを参照して変数を使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="4ff1d-107">オブジェクトのメンバーにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="4ff1d-107">To access members of an object</span></span>  
  
-   <span data-ttu-id="4ff1d-108">メンバー アクセス演算子を使用 (`.`) オブジェクトの変数名とメンバー名の間です。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="4ff1d-109">メンバーが場合[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)変数にアクセスする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="4ff1d-110">既知の型のオブジェクトのメンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="4ff1d-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="4ff1d-111">コンパイル時にオブジェクトの種類を把握している場合を使えば*事前バインディング*それを参照している変数のです。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="4ff1d-112">コンパイル時に型を認識するオブジェクトのメンバーにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="4ff1d-112">To access members of an object for which you know the type at compile time</span></span>  
  
1.  <span data-ttu-id="4ff1d-113">変数に代入するオブジェクトの型にするオブジェクト変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="4ff1d-114">`Option Strict On`、のみ割り当てることができます<xref:System.Windows.Forms.Form>オブジェクト (またはから派生した型のオブジェクトを<xref:System.Windows.Forms.Form>) に`extraForm`です。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="4ff1d-115">クラスまたは拡大は、変換を含む構造体を定義するかどうか`CType`への変換<xref:System.Windows.Forms.Form>、することができますもそのクラスを割り当てるモデルまたは構造に`extraForm`です。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2.  <span data-ttu-id="4ff1d-116">メンバー アクセス演算子を使用 (`.`) オブジェクトの変数名とメンバー名の間です。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="4ff1d-117">メソッドとプロパティに固有のすべてにアクセスすることができます、<xref:System.Windows.Forms.Form>新機能に関係なく、クラス、`Option Strict`設定します。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="4ff1d-118">不明な型のオブジェクトのメンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="4ff1d-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="4ff1d-119">使用する必要があるコンパイル時に、オブジェクトの型がわからない場合*遅延バインディング*の任意の変数を参照しています。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="4ff1d-120">対象のわからない型コンパイル時にオブジェクトのメンバーにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="4ff1d-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1.  <span data-ttu-id="4ff1d-121">オブジェクト変数を宣言である、[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="4ff1d-122">(として変数を宣言する`Object`として宣言することと同じ<xref:System.Object?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="4ff1d-123">`Option Strict On`で定義されているメンバーのみにアクセスすることができます、<xref:System.Object>クラスです。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2.  <span data-ttu-id="4ff1d-124">メンバー アクセス演算子を使用 (`.`) オブジェクトの変数名とメンバー名の間です。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="4ff1d-125">オブジェクト変数に代入する任意のオブジェクトのメンバーにアクセスできるようにするには、設定する必要があります`Option Strict Off`です。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="4ff1d-126">これを行うと、コンパイラが指定されたメンバーが変数に割り当てるオブジェクトによって公開されることを保証することはできません。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="4ff1d-127">オブジェクトにアクセスしようとするメンバーを公開していない場合、<xref:System.MemberAccessException>例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="4ff1d-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff1d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ff1d-128">See Also</span></span>  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [<span data-ttu-id="4ff1d-129">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="4ff1d-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="4ff1d-130">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="4ff1d-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="4ff1d-131">Object 型</span><span class="sxs-lookup"><span data-stu-id="4ff1d-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="4ff1d-132">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="4ff1d-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
