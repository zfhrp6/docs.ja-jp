---
title: "Property ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
dev_langs:
- VB
helpviewer_keywords:
- Property statement
- default modifier
- property procedures, Property statements
- Property keyword
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
caps.latest.revision: 41
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: dbd779b4b6a1dd167e8581066b0fbe034cd2d8f2
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="property-statement"></a><span data-ttu-id="19e4d-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="19e4d-102">Property Statement</span></span>
<span data-ttu-id="19e4d-103">プロパティの名前、およびプロパティの値を格納して取得するために使用されるプロパティ プロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19e4d-104">構文</span><span class="sxs-lookup"><span data-stu-id="19e4d-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="19e4d-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="19e4d-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="19e4d-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-106">Optional.</span></span> <span data-ttu-id="19e4d-107">このプロパティに適用される属性の一覧または`Get`または`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="19e4d-108">参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="19e4d-109">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-109">Optional.</span></span> <span data-ttu-id="19e4d-110">このプロパティは、クラスまたは構造体が定義されている既定のプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="19e4d-111">既定のプロパティのパラメーターを受け入れる必要がありに設定してプロパティ名を指定しなくても取得します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="19e4d-112">としてプロパティを宣言する場合は、 `Default`、使用することはできません`Private`プロパティまたはプロパティ プロシージャのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="19e4d-113">省略可能な`Property`ステートメントの&1; つだけで、`Get`と`Set`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="19e4d-114">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="19e4d-115">Public</span><span class="sxs-lookup"><span data-stu-id="19e4d-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="19e4d-116">Protected</span><span class="sxs-lookup"><span data-stu-id="19e4d-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="19e4d-117">Friend</span><span class="sxs-lookup"><span data-stu-id="19e4d-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="19e4d-118">Private</span><span class="sxs-lookup"><span data-stu-id="19e4d-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="19e4d-119">参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-119">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="19e4d-120">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-120">Optional.</span></span> <span data-ttu-id="19e4d-121">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="19e4d-122">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="19e4d-122">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="19e4d-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="19e4d-123">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="19e4d-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="19e4d-124">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="19e4d-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="19e4d-125">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="19e4d-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="19e4d-126">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="19e4d-127">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-127">Optional.</span></span> <span data-ttu-id="19e4d-128">参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-128">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="19e4d-129">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-129">Optional.</span></span> <span data-ttu-id="19e4d-130">参照してください[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-130">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="19e4d-131">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-131">Optional.</span></span> <span data-ttu-id="19e4d-132">参照してください[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-132">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="19e4d-133">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-133">Optional.</span></span> <span data-ttu-id="19e4d-134">参照してください[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-134">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="19e4d-135">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-135">Optional.</span></span> <span data-ttu-id="19e4d-136">参照してください[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-136">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="19e4d-137">必須です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-137">Required.</span></span> <span data-ttu-id="19e4d-138">プロパティ名。</span><span class="sxs-lookup"><span data-stu-id="19e4d-138">Name of the property.</span></span> <span data-ttu-id="19e4d-139">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-139">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="19e4d-140">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-140">Optional.</span></span> <span data-ttu-id="19e4d-141">このプロパティのパラメーターとの可能な追加パラメーターを表すローカル変数名の一覧、`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-141">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="19e4d-142">参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-142">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="19e4d-143">必要な場合`Option``Strict`は`On`です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-143">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="19e4d-144">このプロパティによって返される値のデータ型。</span><span class="sxs-lookup"><span data-stu-id="19e4d-144">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="19e4d-145">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-145">Optional.</span></span> <span data-ttu-id="19e4d-146">このプロパティには、このプロパティを含むクラスまたは構造体によって実装されるインターフェイスで定義されている&1; つずつ、1 つまたは複数のプロパティが実装していることを示します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-146">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="19e4d-147">参照してください[ステートメントを実装します](../../../visual-basic/language-reference/statements/implements-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-147">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="19e4d-148">`Implements` を指定する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="19e4d-149">実装されているプロパティの一覧。</span><span class="sxs-lookup"><span data-stu-id="19e4d-149">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="19e4d-150">`implementedproperty` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-150">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="19e4d-151">パーツ</span><span class="sxs-lookup"><span data-stu-id="19e4d-151">Part</span></span>|<span data-ttu-id="19e4d-152">説明</span><span class="sxs-lookup"><span data-stu-id="19e4d-152">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="19e4d-153">必須です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-153">Required.</span></span> <span data-ttu-id="19e4d-154">このプロパティによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-154">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="19e4d-155">必須です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-155">Required.</span></span> <span data-ttu-id="19e4d-156">名前のプロパティを定義する`interface`です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-156">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="19e4d-157">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-157">Optional.</span></span> <span data-ttu-id="19e4d-158">プロパティがマークされているかどうかに必要な`WriteOnly`です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-158">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="19e4d-159">開始、`Get`プロパティの値を返すために使用するプロパティ プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-159">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="19e4d-160">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-160">Optional.</span></span> <span data-ttu-id="19e4d-161">内で実行するステートメントのブロック、`Get`または`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-161">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="19e4d-162">終了、`Get`プロパティ プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-162">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="19e4d-163">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-163">Optional.</span></span> <span data-ttu-id="19e4d-164">プロパティがマークされているかどうかに必要な`ReadOnly`です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-164">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="19e4d-165">開始、`Set`プロパティ プロシージャ、プロパティの値を格納するために使用します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-165">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="19e4d-166">終了、`Set`プロパティ プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-166">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="19e4d-167">このプロパティの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-167">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19e4d-168">コメント</span><span class="sxs-lookup"><span data-stu-id="19e4d-168">Remarks</span></span>  
 <span data-ttu-id="19e4d-169">`Property`ステートメントは、プロパティの宣言を導入します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-169">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="19e4d-170">プロパティがあることができます、`Get`プロシージャ (読み取り専用)、`Set`プロシージャ (書き込み専用)、または両方 (読み取り/書き込み)。</span><span class="sxs-lookup"><span data-stu-id="19e4d-170">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="19e4d-171">省略することができます、`Get`と`Set`プロシージャは、自動実装プロパティを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="19e4d-171">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="19e4d-172">詳細については、次を参照してください。 [Auto-Implemented プロパティ](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-172">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="19e4d-173">使用する`Property`クラス レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-173">You can use `Property` only at class level.</span></span> <span data-ttu-id="19e4d-174">つまり、*宣言コンテキスト*プロパティは、クラス、構造体、モジュール、またはインターフェイスである必要があり、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="19e4d-174">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="19e4d-175">詳細については、次を参照してください。[宣言コンテキストとアクセス レベルの既定の](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-175">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="19e4d-176">既定では、プロパティは、パブリック アクセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-176">By default, properties use public access.</span></span> <span data-ttu-id="19e4d-177">アクセス修飾子を使って、このプロパティのアクセス レベルを調整することができます、`Property`ステートメント、および、必要に応じて調整できますより制限の厳しいアクセス レベルは、プロパティ プロシージャのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-177">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="19e4d-178">Visual Basic のパラメーターを渡す、`Set`プロパティを設定中にプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-178">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="19e4d-179">パラメーターを指定しない場合`Set`、統合開発環境 (IDE) という名前の暗黙のパラメーターを使用して`value`します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-179">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="19e4d-180">このパラメーターは、プロパティに割り当てられる値を保持します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-180">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="19e4d-181">通常、この値は、プライベートなローカル変数に格納およびそれを返すときに、`Get`プロシージャが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="19e4d-181">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="19e4d-182">ルール</span><span class="sxs-lookup"><span data-stu-id="19e4d-182">Rules</span></span>  
  
-   <span data-ttu-id="19e4d-183">**混合アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="19e4d-183">**Mixed Access Levels.**</span></span> <span data-ttu-id="19e4d-184">必要に応じていずれかの異なるアクセス レベルを指定することができます読み取り/書き込みプロパティを定義する場合、`Get`または`Set`プロシージャが、どちらかです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-184">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="19e4d-185">これを行うと、プロシージャのアクセス レベルが、プロパティのアクセスのレベル以上に制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19e4d-185">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="19e4d-186">例では、このプロパティが宣言されている場合の`Friend`、宣言することができます、`Set`プロシージャ`Private`、ではなく`Public`です。</span><span class="sxs-lookup"><span data-stu-id="19e4d-186">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="19e4d-187">定義する場合は、`ReadOnly`または`WriteOnly`プロパティ、1 つのプロパティのプロシージャ (`Get`または`Set`、それぞれ) すべてのプロパティを表します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-187">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="19e4d-188">プロパティの&2; つのアクセス レベルを設定することがあるために、このような手順は、異なるアクセス レベルを宣言できません。</span><span class="sxs-lookup"><span data-stu-id="19e4d-188">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="19e4d-189">**型を返します。**</span><span class="sxs-lookup"><span data-stu-id="19e4d-189">**Return Type.**</span></span> <span data-ttu-id="19e4d-190">`Property`ステートメントで返される値のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="19e4d-190">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="19e4d-191">任意のデータ型または列挙型、構造体、クラス、インターフェイスの名前を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="19e4d-191">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="19e4d-192">指定しない場合`returntype`、プロパティの戻り値を`Object`します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-192">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="19e4d-193">**実装です。**</span><span class="sxs-lookup"><span data-stu-id="19e4d-193">**Implementation.**</span></span> <span data-ttu-id="19e4d-194">このプロパティで使用する場合、`Implements`キーワードを含むクラスまたは構造体が必要、`Implements`直後のステートメントの`Class`または`Structure`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-194">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="19e4d-195">`Implements`ステートメントで指定された各インターフェイスを含める必要があります`implementslist`します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-195">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="19e4d-196">ただし、インターフェイスを定義する名前、 `Property` (で`definedname`) すると、このプロパティの名前と同じである必要はありません (で`name`)。</span><span class="sxs-lookup"><span data-stu-id="19e4d-196">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="19e4d-197">動作</span><span class="sxs-lookup"><span data-stu-id="19e4d-197">Behavior</span></span>  
  
-   <span data-ttu-id="19e4d-198">**プロパティ プロシージャから取得します。**</span><span class="sxs-lookup"><span data-stu-id="19e4d-198">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="19e4d-199">ときに、`Get`または`Set`それを呼び出し元ステートメントの次のステートメントと、プロシージャ呼び出し元のコードに戻ると、実行が継続します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-199">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="19e4d-200">`Exit Property`と`Return`ステートメントでは、プロパティ プロシージャからすぐに終了します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-200">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="19e4d-201">任意の数の`Exit Property`と`Return`ステートメントが任意の場所で、手順と混在させることが`Exit Property`と`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-201">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="19e4d-202">**値を返します。**</span><span class="sxs-lookup"><span data-stu-id="19e4d-202">**Return Value.**</span></span> <span data-ttu-id="19e4d-203">値を返す、`Get`プロシージャ、プロパティ名に値を割り当てるか、含めることで、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-203">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="19e4d-204">次の例では、戻り値を割り当てて、プロパティ名に`quoteForTheDay`し、使用して、`Exit Property`を返すステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19e4d-204">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     <span data-ttu-id="19e4d-205">[!code-vb[VbVbalrStatements #&27;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="19e4d-205">[!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span></span>  
  
     <span data-ttu-id="19e4d-206">[!code-vb[VbVbalrStatements #&28;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="19e4d-206">[!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]</span></span>  
  
     <span data-ttu-id="19e4d-207">使用する場合`Exit Property`、値を割り当てることがなく`name`、`Get`プロシージャは、このプロパティのデータ型の既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="19e4d-208">`Return`同時ステートメントは、代入、`Get`プロシージャを返す値し、手順を終了します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="19e4d-209">次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-209">The following example shows this.</span></span>  
  
     <span data-ttu-id="19e4d-210">[!code-vb[VbVbalrStatements #&27;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="19e4d-210">[!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span></span>  
  
     <span data-ttu-id="19e4d-211">[!code-vb[VbVbalrStatements #&29;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="19e4d-211">[!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="19e4d-212">例</span><span class="sxs-lookup"><span data-stu-id="19e4d-212">Example</span></span>  
 <span data-ttu-id="19e4d-213">次の例では、クラスのプロパティを宣言します。</span><span class="sxs-lookup"><span data-stu-id="19e4d-213">The following example declares a property in a class.</span></span>  
  
 <span data-ttu-id="19e4d-214">[!code-vb[VbVbalrStatements&51;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="19e4d-214">[!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e4d-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="19e4d-215">See Also</span></span>  
 <span data-ttu-id="19e4d-216">[自動実装プロパティ](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span><span class="sxs-lookup"><span data-stu-id="19e4d-216">[Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span></span>  
<span data-ttu-id="19e4d-217"> [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="19e4d-217"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="19e4d-218"> [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="19e4d-218"> [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="19e4d-219"> [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md) </span><span class="sxs-lookup"><span data-stu-id="19e4d-219"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) </span></span>  
<span data-ttu-id="19e4d-220"> [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="19e4d-220"> [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) </span></span>  
<span data-ttu-id="19e4d-221"> [既定値](../../../visual-basic/language-reference/modifiers/default.md)</span><span class="sxs-lookup"><span data-stu-id="19e4d-221"> [Default](../../../visual-basic/language-reference/modifiers/default.md)</span></span>

