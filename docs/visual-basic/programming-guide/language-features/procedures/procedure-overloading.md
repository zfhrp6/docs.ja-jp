---
title: "プロシージャのオーバーロード (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65fd5a6763752c616f13891bfa5acabff6115d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="c5f4b-102">プロシージャのオーバーロード (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5f4b-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="c5f4b-103">*オーバー ロード*プロシージャでは、異なるパラメーター リストが同じ名前を使用して、複数のバージョンでそれを定義することを意味します。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="c5f4b-104">オーバー ロードの目的では、名前で区別することがなく密接に関連するいくつかのバージョンのプロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="c5f4b-105">こうと、パラメーター リストを変更します。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="c5f4b-106">オーバー ロードの規則</span><span class="sxs-lookup"><span data-stu-id="c5f4b-106">Overloading Rules</span></span>  
 <span data-ttu-id="c5f4b-107">プロシージャをオーバー ロードする場合は、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="c5f4b-108">**同じ名前**です。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-108">**Same Name**.</span></span> <span data-ttu-id="c5f4b-109">各オーバー ロードされたバージョンでは、同じプロシージャ名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="c5f4b-110">**異なるシグネチャ**です。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-110">**Different Signature**.</span></span> <span data-ttu-id="c5f4b-111">各オーバー ロードされたバージョンは、次のうちの少なくとも 1 つにその他のすべてのオーバー ロードされたバージョンと異なって必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="c5f4b-112">パラメーターの数</span><span class="sxs-lookup"><span data-stu-id="c5f4b-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="c5f4b-113">パラメーターの順序</span><span class="sxs-lookup"><span data-stu-id="c5f4b-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="c5f4b-114">パラメーターのデータ型</span><span class="sxs-lookup"><span data-stu-id="c5f4b-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="c5f4b-115">型パラメーター (ジェネリック プロシージャの場合) の数</span><span class="sxs-lookup"><span data-stu-id="c5f4b-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="c5f4b-116">戻り値の型 (変換演算子) の場合のみ</span><span class="sxs-lookup"><span data-stu-id="c5f4b-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="c5f4b-117">プロシージャ名と前の項目は、総称、*署名*プロシージャのです。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="c5f4b-118">オーバー ロードされたプロシージャを呼び出すときに、コンパイラは、呼び出しが、定義を正しくと一致することを確認するのに署名を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="c5f4b-119">**署名に含まれない項目**です。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="c5f4b-120">シグネチャを変更せず、プロシージャをオーバー ロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="c5f4b-121">具体的には、プロシージャをオーバー ロードするだけで、次の項目には、1 つ以上ことはできません。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="c5f4b-122">プロシージャ修飾子キーワードなど`Public`、 `Shared`、および`Static`</span><span class="sxs-lookup"><span data-stu-id="c5f4b-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="c5f4b-123">パラメーターまたは型のパラメーター名</span><span class="sxs-lookup"><span data-stu-id="c5f4b-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="c5f4b-124">型パラメーターの制約 (ジェネリック プロシージャ) の場合</span><span class="sxs-lookup"><span data-stu-id="c5f4b-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="c5f4b-125">パラメーター修飾子キーワードなど`ByRef`と`Optional`</span><span class="sxs-lookup"><span data-stu-id="c5f4b-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="c5f4b-126">値を返すかどうか</span><span class="sxs-lookup"><span data-stu-id="c5f4b-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="c5f4b-127">(変換演算子) を除く、戻り値のデータ型</span><span class="sxs-lookup"><span data-stu-id="c5f4b-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="c5f4b-128">上記のリスト内の項目は、シグネチャの一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="c5f4b-129">オーバー ロードされたバージョンを区別するために、使用することはできません、それぞれのシグネチャによって区別されるオーバー ロードされたバージョン間でそれらを変更できます。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="c5f4b-130">**遅延バインディング引数**です。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="c5f4b-131">オーバー ロードされたバージョンに遅延バインディング オブジェクト変数を渡す場合は、適切なパラメーターとしてを宣言する必要があります<xref:System.Object>です。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="c5f4b-132">プロシージャの複数のバージョン</span><span class="sxs-lookup"><span data-stu-id="c5f4b-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="c5f4b-133">作成するいるとすると、`Sub`して、顧客の残高に対してトランザクションをポストする手順をしたい名前で、またはアカウント数によって、顧客を参照することです。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="c5f4b-134">これに合わせてを定義できます 2 つの異なる`Sub`例を次の手順。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a><span data-ttu-id="c5f4b-135">オーバー ロードされたバージョン</span><span class="sxs-lookup"><span data-stu-id="c5f4b-135">Overloaded Versions</span></span>  
 <span data-ttu-id="c5f4b-136">代わりに、1 つのプロシージャ名をオーバー ロードを開始します。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="c5f4b-137">使用することができます、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワードを次のように各パラメーター一覧については、プロシージャのバージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a><span data-ttu-id="c5f4b-138">オーバー ロードを追加</span><span class="sxs-lookup"><span data-stu-id="c5f4b-138">Additional Overloads</span></span>  
 <span data-ttu-id="c5f4b-139">いずれかでトランザクションの量をそのまま使用したい場合`Decimal`または`Single`、オーバー ロードすることがさらに`post`このバリエーションに使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="c5f4b-140">これを行った場合、前の例でオーバー ロードの各グループにする必要が 4 つ`Sub`4 つの異なるシグネチャを持つが、同じ名前のすべての手順です。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="c5f4b-141">オーバー ロードの利点</span><span class="sxs-lookup"><span data-stu-id="c5f4b-141">Advantages of Overloading</span></span>  
 <span data-ttu-id="c5f4b-142">プロシージャのオーバー ロードの利点は、呼び出しの柔軟性にです。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="c5f4b-143">使用する、`post`プロシージャで宣言されている前の例では、呼び出し元のコードは、いずれかとして、顧客 id を取得できます、`String`または`Integer`、どちらの場合、同じプロシージャを呼び出すとします。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="c5f4b-144">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-144">The following example illustrates this:</span></span>  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c5f4b-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5f4b-145">See Also</span></span>  
 [<span data-ttu-id="c5f4b-146">手順</span><span class="sxs-lookup"><span data-stu-id="c5f4b-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="c5f4b-147">方法 : プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="c5f4b-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="c5f4b-148">方法 : オーバーロードされたプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="c5f4b-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="c5f4b-149">方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="c5f4b-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="c5f4b-150">方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="c5f4b-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="c5f4b-151">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="c5f4b-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="c5f4b-152">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="c5f4b-152">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="c5f4b-153">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="c5f4b-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="c5f4b-154">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="c5f4b-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
