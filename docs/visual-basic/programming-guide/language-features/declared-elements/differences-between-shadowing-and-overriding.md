---
title: "シャドウとオーバーライドの違い (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d67486d9c6af96d314abad7142ba86779d74f5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a><span data-ttu-id="b3c36-102">シャドウとオーバーライドの違い (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3c36-102">Differences Between Shadowing and Overriding (Visual Basic)</span></span>
<span data-ttu-id="b3c36-103">基底クラスから継承するクラスを定義するときする場合がありますを再定義する 1 つまたは複数の派生クラスで基底クラス要素。</span><span class="sxs-lookup"><span data-stu-id="b3c36-103">When you define a class that inherits from a base class, you sometimes want to redefine one or more of the base class elements in the derived class.</span></span> <span data-ttu-id="b3c36-104">シャドウとオーバーライドは、この目的では両方の使用可能なです。</span><span class="sxs-lookup"><span data-stu-id="b3c36-104">Shadowing and overriding are both available for this purpose.</span></span>  
  
## <a name="comparison"></a><span data-ttu-id="b3c36-105">比較</span><span class="sxs-lookup"><span data-stu-id="b3c36-105">Comparison</span></span>  
 <span data-ttu-id="b3c36-106">シャドウとオーバーライドが使用されている場合、派生クラスは、基底クラスから継承し、1 つの宣言された要素と他の再定義します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-106">Shadowing and overriding are both used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="b3c36-107">2 つの重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="b3c36-107">But there are significant differences between the two.</span></span>  
  
 <span data-ttu-id="b3c36-108">次の表では、シャドウとオーバーライドを比較します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-108">The following table compares shadowing with overriding.</span></span>  
  
||||  
|---|---|---|  
|<span data-ttu-id="b3c36-109">比較のポイント</span><span class="sxs-lookup"><span data-stu-id="b3c36-109">Point of comparison</span></span>|<span data-ttu-id="b3c36-110">シャドウ</span><span class="sxs-lookup"><span data-stu-id="b3c36-110">Shadowing</span></span>|<span data-ttu-id="b3c36-111">オーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b3c36-111">Overriding</span></span>|  
|<span data-ttu-id="b3c36-112">目的</span><span class="sxs-lookup"><span data-stu-id="b3c36-112">Purpose</span></span>|<span data-ttu-id="b3c36-113">派生クラスで既に定義されているメンバーを導入する後続の基本クラスの変更から保護します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-113">Protects against a subsequent base-class modification that introduces a member you have already defined in your derived class</span></span>|<span data-ttu-id="b3c36-114">プロシージャまたはプロパティが同じ呼び出し元のシーケンスの別の実装を定義することによって、ポリモーフィズムを実現<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b3c36-114">Achieves polymorphism by defining a different implementation of a procedure or property with the same calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="b3c36-115">再定義された要素</span><span class="sxs-lookup"><span data-stu-id="b3c36-115">Redefined element</span></span>|<span data-ttu-id="b3c36-116">宣言されたいずれかの要素型</span><span class="sxs-lookup"><span data-stu-id="b3c36-116">Any declared element type</span></span>|<span data-ttu-id="b3c36-117">プロシージャのみ (`Function`、 `Sub`、または`Operator`) またはプロパティ</span><span class="sxs-lookup"><span data-stu-id="b3c36-117">Only a procedure (`Function`, `Sub`, or `Operator`) or property</span></span>|  
|<span data-ttu-id="b3c36-118">再定義する要素</span><span class="sxs-lookup"><span data-stu-id="b3c36-118">Redefining element</span></span>|<span data-ttu-id="b3c36-119">宣言されたいずれかの要素型</span><span class="sxs-lookup"><span data-stu-id="b3c36-119">Any declared element type</span></span>|<span data-ttu-id="b3c36-120">プロシージャまたは呼び出しシーケンスが同じプロパティのみ<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b3c36-120">Only a procedure or property with the identical calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="b3c36-121">再定義する要素のアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="b3c36-121">Access level of redefining element</span></span>|<span data-ttu-id="b3c36-122">任意のアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="b3c36-122">Any access level</span></span>|<span data-ttu-id="b3c36-123">上書きされた要素のアクセス レベルを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="b3c36-123">Cannot change access level of overridden element</span></span>|  
|<span data-ttu-id="b3c36-124">読みやすさと再定義する要素の書き込みの許可</span><span class="sxs-lookup"><span data-stu-id="b3c36-124">Readability and writability of redefining element</span></span>|<span data-ttu-id="b3c36-125">任意の組み合わせ</span><span class="sxs-lookup"><span data-stu-id="b3c36-125">Any combination</span></span>|<span data-ttu-id="b3c36-126">読みやすさやすさのオーバーライドされたプロパティを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="b3c36-126">Cannot change readability or writability of overridden property</span></span>|  
|<span data-ttu-id="b3c36-127">再定義の制御します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-127">Control over redefining</span></span>|<span data-ttu-id="b3c36-128">基底クラス要素は、強制またはシャドウを禁止することはできません。</span><span class="sxs-lookup"><span data-stu-id="b3c36-128">Base class element cannot enforce or prohibit shadowing</span></span>|<span data-ttu-id="b3c36-129">基底クラス要素を指定できます`MustOverride`、 `NotOverridable`、または`Overridable`</span><span class="sxs-lookup"><span data-stu-id="b3c36-129">Base class element can specify `MustOverride`, `NotOverridable`, or `Overridable`</span></span>|  
|<span data-ttu-id="b3c36-130">キーワードの使用法</span><span class="sxs-lookup"><span data-stu-id="b3c36-130">Keyword usage</span></span>|<span data-ttu-id="b3c36-131">`Shadows`派生クラスでは推奨`Shadows`どちらもと見なされます`Shadows`も`Overrides`指定<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b3c36-131">`Shadows` recommended in derived class; `Shadows` assumed if neither `Shadows` nor `Overrides` specified<sup>2</sup></span></span>|<span data-ttu-id="b3c36-132">`Overridable`または`MustOverride`基本クラスでは必須`Overrides`派生クラスで必要</span><span class="sxs-lookup"><span data-stu-id="b3c36-132">`Overridable` or `MustOverride` required in base class; `Overrides` required in derived class</span></span>|  
|<span data-ttu-id="b3c36-133">派生クラスから派生するクラスで再定義する要素の継承</span><span class="sxs-lookup"><span data-stu-id="b3c36-133">Inheritance of redefining element by classes deriving from your derived class</span></span>|<span data-ttu-id="b3c36-134">継承された要素をシャドウ以降の派生クラスです。シャドウされた要素を非表示のまま<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b3c36-134">Shadowing element inherited by further derived classes; shadowed element still hidden<sup>3</sup></span></span>|<span data-ttu-id="b3c36-135">継承された要素をオーバーライドするさらに派生クラスです。まだオーバーライド上書きされた要素</span><span class="sxs-lookup"><span data-stu-id="b3c36-135">Overriding element inherited by further derived classes; overridden element still overridden</span></span>|  
  
 <span data-ttu-id="b3c36-136"><sup>1</sup> 、*コーリング シーケンス*要素型で構成されます (`Function`、 `Sub`、 `Operator`、または`Property`)、パラメーター リストの名前および戻り型。</span><span class="sxs-lookup"><span data-stu-id="b3c36-136"><sup>1</sup> The *calling sequence* consists of the element type (`Function`, `Sub`, `Operator`, or `Property`), name, parameter list, and return type.</span></span> <span data-ttu-id="b3c36-137">プロパティ、またはその逆を持つプロシージャをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b3c36-137">You cannot override a procedure with a property, or the other way around.</span></span> <span data-ttu-id="b3c36-138">1 つの種類のプロシージャをオーバーライドすることはできません (`Function`、 `Sub`、または`Operator`) 別の種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-138">You cannot override one kind of procedure (`Function`, `Sub`, or `Operator`) with another kind.</span></span>  
  
 <span data-ttu-id="b3c36-139"><sup>2</sup>いずれかを指定しない場合`Shadows`または`Overrides`コンパイラが使用する再定義の種類を確認するために、警告メッセージを発行します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-139"><sup>2</sup> If you do not specify either `Shadows` or `Overrides`, the compiler issues a warning message to help you be sure which kind of redefinition you want to use.</span></span> <span data-ttu-id="b3c36-140">警告を無視する場合は、シャドウ機構が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b3c36-140">If you ignore the warning, the shadowing mechanism is used.</span></span>  
  
 <span data-ttu-id="b3c36-141"><sup>3</sup>シャドウ シャドウする要素がさらに派生クラスでアクセス可能でない場合は継承されません。</span><span class="sxs-lookup"><span data-stu-id="b3c36-141"><sup>3</sup> If the shadowing element is inaccessible in a further derived class, shadowing is not inherited.</span></span> <span data-ttu-id="b3c36-142">シャドウ要素として宣言した場合など、 `Private`、派生クラスから派生したクラスがシャドウ要素ではなく元の要素を継承します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-142">For example, if you declare the shadowing element as `Private`, a class deriving from your derived class inherits the original element instead of the shadowing element.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="b3c36-143">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="b3c36-143">Guidelines</span></span>  
 <span data-ttu-id="b3c36-144">また、次の場合、オーバーライドする通常使用します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-144">You normally use overriding in the following cases:</span></span>  
  
-   <span data-ttu-id="b3c36-145">ポリモーフィックな派生クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-145">You are defining polymorphic derived classes.</span></span>  
  
-   <span data-ttu-id="b3c36-146">安全のために、コンパイラが、同一の要素型と呼び出し元のシーケンスを適用します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-146">You want the safety of having the compiler enforce the identical element type and calling sequence.</span></span>  
  
 <span data-ttu-id="b3c36-147">また、次の場合、シャドウ通常使用します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-147">You normally use shadowing in the following cases:</span></span>  
  
-   <span data-ttu-id="b3c36-148">予想される、基本クラスが変更され、自分のものと同じ名前を使用して要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="b3c36-148">You anticipate that your base class might be modified and define an element using the same name as yours.</span></span>  
  
-   <span data-ttu-id="b3c36-149">要素の型の変更や呼び出しシーケンスの自由度ができます。</span><span class="sxs-lookup"><span data-stu-id="b3c36-149">You want the freedom of changing the element type or calling sequence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c36-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3c36-150">See Also</span></span>  
 [<span data-ttu-id="b3c36-151">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="b3c36-151">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="b3c36-152">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="b3c36-152">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="b3c36-153">方法: 自分で宣言した変数と同じ名前の変数を隠す</span><span class="sxs-lookup"><span data-stu-id="b3c36-153">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [<span data-ttu-id="b3c36-154">方法: 継承された変数を隠す</span><span class="sxs-lookup"><span data-stu-id="b3c36-154">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="b3c36-155">方法: 派生クラスによって非表示になっている変数にアクセスする</span><span class="sxs-lookup"><span data-stu-id="b3c36-155">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="b3c36-156">Shadows</span><span class="sxs-lookup"><span data-stu-id="b3c36-156">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="b3c36-157">Overrides</span><span class="sxs-lookup"><span data-stu-id="b3c36-157">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
