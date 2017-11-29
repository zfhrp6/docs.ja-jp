---
title: "Implements ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1103305ffbf5425d9a6a6a09695437968642710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implements-statement"></a><span data-ttu-id="1e5cf-102">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="1e5cf-102">Implements Statement</span></span>
<span data-ttu-id="1e5cf-103">1 つ以上のインターフェイス、またはインターフェイス メンバーの場合、クラスに実装する必要がありますまたはが表示される構造体の定義を指定します。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e5cf-104">構文</span><span class="sxs-lookup"><span data-stu-id="1e5cf-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="1e5cf-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="1e5cf-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="1e5cf-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-106">Required.</span></span> <span data-ttu-id="1e5cf-107">プロパティ、プロシージャ、およびイベントは、クラスまたは構造体に対応するメンバーによって実装されるインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="1e5cf-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-108">Required.</span></span> <span data-ttu-id="1e5cf-109">実装されるインターフェイスのメンバー。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e5cf-110">コメント</span><span class="sxs-lookup"><span data-stu-id="1e5cf-110">Remarks</span></span>  
 <span data-ttu-id="1e5cf-111">インターフェイスは、コレクションのプロトタイプのメンバー (プロパティ、プロシージャ、およびイベント) を表すインターフェイスをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="1e5cf-112">インターフェイスにメンバーの宣言のみを含めるクラスと構造体は、これらのメンバーを実装します。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="1e5cf-113">詳細については、「[インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="1e5cf-114">`Implements`ステートメントの直後に続く必要があります、`Class`または`Structure`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="1e5cf-115">インターフェイスを実装する場合は、インターフェイスで宣言されているすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="1e5cf-116">任意のメンバーを省略することは、構文エラーであると見なされます。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="1e5cf-117">指定する個々 のメンバーを実装する、 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)キーワード (これとは別、`Implements`ステートメント) クラスまたは構造体のメンバーを宣言する場合。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="1e5cf-118">詳細については、「[インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="1e5cf-119">クラスに使用できる[プライベート](../../../visual-basic/language-reference/modifiers/private.md)プロパティと、プロシージャが、これらのメンバーの実装が変数に実装するクラスのインスタンスとして宣言されたインターフェイスの型のキャストによってのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e5cf-120">例</span><span class="sxs-lookup"><span data-stu-id="1e5cf-120">Example</span></span>  
 <span data-ttu-id="1e5cf-121">次の例を使用する方法を示しています、`Implements`インターフェイスのメンバーを実装するステートメント。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="1e5cf-122">という名前のインターフェイスを定義`ICustomerInfo`イベント、プロパティ、およびプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="1e5cf-123">クラス`customerInfo`インターフェイスで定義されているすべてのメンバーを実装します。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 <span data-ttu-id="1e5cf-124">なおクラス`customerInfo`を使用して、`Implements`クラスが、一部のメンバーを実装することを示すために別のソース コード行のステートメントで、`ICustomerInfo`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="1e5cf-125">クラス内の各メンバーを使用して、`Implements`そのインターフェイスのメンバーを実装することを示すために、メンバー宣言の一部としてキーワード。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e5cf-126">例</span><span class="sxs-lookup"><span data-stu-id="1e5cf-126">Example</span></span>  
 <span data-ttu-id="1e5cf-127">次の 2 つの手順では、前の例で実装されるインターフェイスを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="1e5cf-128">実装をテストするには、呼び出しをプロジェクトにこれらの手順を追加、`testImplements`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="1e5cf-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1e5cf-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e5cf-129">See Also</span></span>  
 [<span data-ttu-id="1e5cf-130">Implements</span><span class="sxs-lookup"><span data-stu-id="1e5cf-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [<span data-ttu-id="1e5cf-131">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="1e5cf-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="1e5cf-132">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e5cf-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
