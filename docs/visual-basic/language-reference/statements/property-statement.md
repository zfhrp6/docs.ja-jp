---
title: Property Statement
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 3f3ced3f0c441518594820f75243c71fb0c3babd
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="property-statement"></a><span data-ttu-id="19a47-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="19a47-102">Property Statement</span></span>
<span data-ttu-id="19a47-103">プロパティ、および格納およびプロパティの値を取得するためのプロパティ プロシージャの名前を宣言します。</span><span class="sxs-lookup"><span data-stu-id="19a47-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19a47-104">構文</span><span class="sxs-lookup"><span data-stu-id="19a47-104">Syntax</span></span>  
  
```vb  
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
  
## <a name="parts"></a><span data-ttu-id="19a47-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="19a47-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="19a47-106">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-106">Optional.</span></span> <span data-ttu-id="19a47-107">このプロパティに適用される属性の一覧または`Get`または`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19a47-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="19a47-108">参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="19a47-109">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-109">Optional.</span></span> <span data-ttu-id="19a47-110">このプロパティは、既定のプロパティをクラスまたは構造体が定義されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="19a47-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="19a47-111">既定のプロパティのパラメーターを受け入れる必要がありますとに設定してプロパティ名を指定しなくても取得します。</span><span class="sxs-lookup"><span data-stu-id="19a47-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="19a47-112">としてプロパティを宣言する場合`Default`、使用することはできません`Private`プロパティまたはプロパティ プロシージャのいずれか。</span><span class="sxs-lookup"><span data-stu-id="19a47-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="19a47-113">省略可能な`Property`ステートメントおよび最大で 1 つの`Get`と`Set`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19a47-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="19a47-114">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="19a47-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="19a47-115">Public</span><span class="sxs-lookup"><span data-stu-id="19a47-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="19a47-116">Protected</span><span class="sxs-lookup"><span data-stu-id="19a47-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="19a47-117">Friend</span><span class="sxs-lookup"><span data-stu-id="19a47-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="19a47-118">Private</span><span class="sxs-lookup"><span data-stu-id="19a47-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="19a47-119">保護されたフレンド</span><span class="sxs-lookup"><span data-stu-id="19a47-119">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md) 

    - [<span data-ttu-id="19a47-120">保護されたプライベート</span><span class="sxs-lookup"><span data-stu-id="19a47-120">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="19a47-121">参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-121">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="19a47-122">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-122">Optional.</span></span> <span data-ttu-id="19a47-123">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="19a47-123">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="19a47-124">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="19a47-124">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="19a47-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="19a47-125">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="19a47-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="19a47-126">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="19a47-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="19a47-127">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="19a47-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="19a47-128">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="19a47-129">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-129">Optional.</span></span> <span data-ttu-id="19a47-130">参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-130">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="19a47-131">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-131">Optional.</span></span> <span data-ttu-id="19a47-132">参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-132">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="19a47-133">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-133">Optional.</span></span> <span data-ttu-id="19a47-134">参照してください[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-134">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="19a47-135">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-135">Optional.</span></span> <span data-ttu-id="19a47-136">参照してください[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-136">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="19a47-137">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-137">Optional.</span></span> <span data-ttu-id="19a47-138">参照してください[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-138">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="19a47-139">必須。</span><span class="sxs-lookup"><span data-stu-id="19a47-139">Required.</span></span> <span data-ttu-id="19a47-140">プロパティ名。</span><span class="sxs-lookup"><span data-stu-id="19a47-140">Name of the property.</span></span> <span data-ttu-id="19a47-141">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-141">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="19a47-142">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-142">Optional.</span></span> <span data-ttu-id="19a47-143">このプロパティのパラメーターとの考えられる追加のパラメーターを表すローカル変数名の一覧、`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19a47-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="19a47-144">参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-144">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="19a47-145">場合は必須`Option``Strict`は`On`します。</span><span class="sxs-lookup"><span data-stu-id="19a47-145">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="19a47-146">このプロパティによって返される値のデータ型。</span><span class="sxs-lookup"><span data-stu-id="19a47-146">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="19a47-147">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-147">Optional.</span></span> <span data-ttu-id="19a47-148">このプロパティには、このプロパティの包含クラスまたは構造体によって実装されるインターフェイスで定義されている 1 つずつ、1 つまたは複数のプロパティが実装されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="19a47-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="19a47-149">参照してください[ステートメントを実装します](../../../visual-basic/language-reference/statements/implements-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="19a47-149">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="19a47-150">`Implements` を指定する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="19a47-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="19a47-151">実装されているプロパティの一覧です。</span><span class="sxs-lookup"><span data-stu-id="19a47-151">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="19a47-152">`implementedproperty` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="19a47-152">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="19a47-153">パーツ</span><span class="sxs-lookup"><span data-stu-id="19a47-153">Part</span></span>|<span data-ttu-id="19a47-154">説明</span><span class="sxs-lookup"><span data-stu-id="19a47-154">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="19a47-155">必須。</span><span class="sxs-lookup"><span data-stu-id="19a47-155">Required.</span></span> <span data-ttu-id="19a47-156">このプロパティによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。</span><span class="sxs-lookup"><span data-stu-id="19a47-156">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="19a47-157">必須。</span><span class="sxs-lookup"><span data-stu-id="19a47-157">Required.</span></span> <span data-ttu-id="19a47-158">名前のプロパティを定義する`interface`です。</span><span class="sxs-lookup"><span data-stu-id="19a47-158">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="19a47-159">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-159">Optional.</span></span> <span data-ttu-id="19a47-160">プロパティがマークされているかどうかに必要な`WriteOnly`します。</span><span class="sxs-lookup"><span data-stu-id="19a47-160">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="19a47-161">開始、`Get`プロパティ プロシージャをプロパティの値を返すために使用します。</span><span class="sxs-lookup"><span data-stu-id="19a47-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="19a47-162">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-162">Optional.</span></span> <span data-ttu-id="19a47-163">内で実行するステートメントのブロック、`Get`または`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19a47-163">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="19a47-164">終了、`Get`プロパティ プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19a47-164">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="19a47-165">任意。</span><span class="sxs-lookup"><span data-stu-id="19a47-165">Optional.</span></span> <span data-ttu-id="19a47-166">プロパティがマークされているかどうかに必要な`ReadOnly`します。</span><span class="sxs-lookup"><span data-stu-id="19a47-166">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="19a47-167">開始、`Set`プロパティ プロシージャ、プロパティの値を格納するために使用します。</span><span class="sxs-lookup"><span data-stu-id="19a47-167">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="19a47-168">終了、`Set`プロパティ プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19a47-168">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="19a47-169">このプロパティの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="19a47-169">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19a47-170">コメント</span><span class="sxs-lookup"><span data-stu-id="19a47-170">Remarks</span></span>  
 <span data-ttu-id="19a47-171">`Property`ステートメントには、プロパティの宣言が導入されています。</span><span class="sxs-lookup"><span data-stu-id="19a47-171">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="19a47-172">プロパティを持つことができます、 `Get` (読み取り専用)、プロシージャ、`Set`プロシージャ (書き込み専用)、または両方 (読み取り/書き込み)。</span><span class="sxs-lookup"><span data-stu-id="19a47-172">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="19a47-173">省略することができます、`Get`と`Set`自動実装プロパティを使用する場合、そのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19a47-173">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="19a47-174">詳細については、「[自動実装プロパティ](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19a47-174">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="19a47-175">使用することができます`Property`クラス レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="19a47-175">You can use `Property` only at class level.</span></span> <span data-ttu-id="19a47-176">つまり、*宣言コンテキスト*プロパティは、クラス、構造体、モジュール、またはインターフェイスである必要があり、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="19a47-176">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="19a47-177">詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19a47-177">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="19a47-178">既定では、プロパティは、パブリック アクセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="19a47-178">By default, properties use public access.</span></span> <span data-ttu-id="19a47-179">アクセス修飾子を使って、このプロパティのアクセス レベルを調整することができます、`Property`ステートメント、および、必要に応じて調整できますより制限の厳しいアクセス レベルは、プロパティ プロシージャのいずれか。</span><span class="sxs-lookup"><span data-stu-id="19a47-179">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="19a47-180">Visual Basic のパラメーターを渡す、`Set`プロパティの割り当て時にプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="19a47-180">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="19a47-181">パラメーターを指定しない場合`Set`、統合開発環境 (IDE) という名前の暗黙のパラメーターを使用して`value`です。</span><span class="sxs-lookup"><span data-stu-id="19a47-181">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="19a47-182">このパラメーターは、プロパティに割り当てられる値を保持します。</span><span class="sxs-lookup"><span data-stu-id="19a47-182">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="19a47-183">通常プライベート ローカル変数にこの値を格納して返すたびに、`Get`プロシージャが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="19a47-183">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="19a47-184">ルール</span><span class="sxs-lookup"><span data-stu-id="19a47-184">Rules</span></span>  
  
-   <span data-ttu-id="19a47-185">**混合アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="19a47-185">**Mixed Access Levels.**</span></span> <span data-ttu-id="19a47-186">必要に応じていずれかの異なるアクセス レベルを指定することができます、読み取り/書き込みプロパティを定義する場合、`Get`または`Set`プロシージャが、両方は使用できません。</span><span class="sxs-lookup"><span data-stu-id="19a47-186">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="19a47-187">これを行うと、プロシージャのアクセス レベルがプロパティのアクセス レベルよりも制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19a47-187">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="19a47-188">プロパティが宣言されている場合など、 `Friend`、宣言することができます、`Set`プロシージャ`Private`、ではなく`Public`です。</span><span class="sxs-lookup"><span data-stu-id="19a47-188">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="19a47-189">定義する場合、`ReadOnly`または`WriteOnly`プロパティ、1 つのプロパティ プロシージャ (`Get`または`Set`、それぞれ) すべてのプロパティを表します。</span><span class="sxs-lookup"><span data-stu-id="19a47-189">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="19a47-190">プロパティの 2 つのアクセス レベルを設定することがあるために、このような手順は、異なるアクセス レベルを宣言できません。</span><span class="sxs-lookup"><span data-stu-id="19a47-190">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="19a47-191">**型を返します。**</span><span class="sxs-lookup"><span data-stu-id="19a47-191">**Return Type.**</span></span> <span data-ttu-id="19a47-192">`Property`ステートメントが返す値のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="19a47-192">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="19a47-193">任意のデータ型または列挙型、構造体、クラス、またはインターフェイスの名前を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="19a47-193">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="19a47-194">指定しない場合`returntype`、プロパティから返される`Object`です。</span><span class="sxs-lookup"><span data-stu-id="19a47-194">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="19a47-195">**実装です。**</span><span class="sxs-lookup"><span data-stu-id="19a47-195">**Implementation.**</span></span> <span data-ttu-id="19a47-196">このプロパティで使用する場合、`Implements`キーワードを含むクラスまたは構造体があります、`Implements`直後のステートメントの`Class`または`Structure`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19a47-196">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="19a47-197">`Implements`ステートメントで指定された各インターフェイスを含める必要があります`implementslist`です。</span><span class="sxs-lookup"><span data-stu-id="19a47-197">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="19a47-198">ただし、インターフェイスを定義する名前、 `Property` (で`definedname`) すると、このプロパティの名前と同じである必要はありません (で`name`)。</span><span class="sxs-lookup"><span data-stu-id="19a47-198">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="19a47-199">動作</span><span class="sxs-lookup"><span data-stu-id="19a47-199">Behavior</span></span>  
  
-   <span data-ttu-id="19a47-200">**プロパティ プロシージャから取得します。**</span><span class="sxs-lookup"><span data-stu-id="19a47-200">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="19a47-201">ときに、`Get`または`Set`起動したステートメントに続くステートメントと、プロシージャ呼び出し元のコードに戻ると、実行が継続します。</span><span class="sxs-lookup"><span data-stu-id="19a47-201">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="19a47-202">`Exit Property`と`Return`ステートメントでは、プロパティ プロシージャからすぐに終了します。</span><span class="sxs-lookup"><span data-stu-id="19a47-202">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="19a47-203">任意の数の`Exit Property`と`Return`ステートメントがどこにでも表示、プロシージャとを混在させること`Exit Property`と`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19a47-203">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="19a47-204">**値を返します。**</span><span class="sxs-lookup"><span data-stu-id="19a47-204">**Return Value.**</span></span> <span data-ttu-id="19a47-205">値を返す、`Get`プロシージャ、プロパティ名に値を割り当てるか、含めることで、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19a47-205">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="19a47-206">次の例では、戻り値を割り当てて、プロパティ名に`quoteForTheDay`しを使用して、`Exit Property`を返すステートメントです。</span><span class="sxs-lookup"><span data-stu-id="19a47-206">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     <span data-ttu-id="19a47-207">使用する場合`Exit Property`、値を割り当てることがなく`name`、`Get`プロシージャは、プロパティのデータ型の既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="19a47-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="19a47-208">`Return`同時ステートメントは、代入、`Get`プロシージャを返す値し、手順を終了します。</span><span class="sxs-lookup"><span data-stu-id="19a47-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="19a47-209">この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19a47-209">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="19a47-210">例</span><span class="sxs-lookup"><span data-stu-id="19a47-210">Example</span></span>  
 <span data-ttu-id="19a47-211">次の例では、クラスのプロパティを宣言します。</span><span class="sxs-lookup"><span data-stu-id="19a47-211">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="19a47-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="19a47-212">See Also</span></span>  
 [<span data-ttu-id="19a47-213">自動実装プロパティ</span><span class="sxs-lookup"><span data-stu-id="19a47-213">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [<span data-ttu-id="19a47-214">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="19a47-214">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="19a47-215">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="19a47-215">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="19a47-216">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="19a47-216">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="19a47-217">パラメーター リスト</span><span class="sxs-lookup"><span data-stu-id="19a47-217">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="19a47-218">既定値</span><span class="sxs-lookup"><span data-stu-id="19a47-218">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
