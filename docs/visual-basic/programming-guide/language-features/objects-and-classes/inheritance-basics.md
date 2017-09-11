---
title: "継承の基本 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- derived classes, inheritance
- MyClass keyword, using
- MyBase keyword, using
- Inherits statement, inheritance
- overriding, Overridable keyword
- MustInherit keyword, using
- Overrides keyword, using
- inheritance
- MustInherit classes
- MustOverride keyword, using
- classes [Visual Basic], derived
- NotInheritable keyword, using
- base classes, extending properties and methods
- NotOverridable keyword, using
- base classes, inheritance
- abstract classes, inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
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
ms.sourcegitcommit: 4892ed6dcfb3843bd6cb2de2d3e032bfeb1efdf9
ms.openlocfilehash: 43b6505634b12f7f8353866e938151f1e00fb073
ms.contentlocale: ja-jp
ms.lasthandoff: 05/16/2017

---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="02c4b-102">継承の基本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02c4b-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="02c4b-103">`Inherits`という新しいクラスを宣言するステートメントが使用される、*クラスを派生*と呼ばれる、既存のクラスに基づいて、*基本クラス*します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="02c4b-104">派生クラスでは、継承、およびプロパティ、メソッド、イベント、フィールド、および基本クラスで定義された定数は、拡張できます。</span><span class="sxs-lookup"><span data-stu-id="02c4b-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="02c4b-105">次のセクションが、継承の規則のいくつかを説明し、方法クラスを変更するのに使用できる修飾子を継承または継承されます。</span><span class="sxs-lookup"><span data-stu-id="02c4b-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
-   <span data-ttu-id="02c4b-106">既定では、すべてクラスは継承とマークされていない限り、`NotInheritable`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="02c4b-107">クラスは、プロジェクト内の他のクラスまたはその他のプロジェクトで参照されるアセンブリのクラスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="02c4b-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
-   <span data-ttu-id="02c4b-108">複数の継承を許可する言語とは異なり[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のみ単一継承クラスでは、1 つの基本クラスを派生クラスでは、あることができます。</span><span class="sxs-lookup"><span data-stu-id="02c4b-108">Unlike languages that allow multiple inheritance, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="02c4b-109">クラスに複数の継承は許可されていませんが、クラスは、複数のインターフェイスは、同じ結果を効果的に実現できますを実装できます。</span><span class="sxs-lookup"><span data-stu-id="02c4b-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
-   <span data-ttu-id="02c4b-110">基底クラスでの制限付きの項目を公開することを防ぐためには、派生クラスのアクセスの種類がありますと等しいかそれより制限の厳しい、基本クラス。</span><span class="sxs-lookup"><span data-stu-id="02c4b-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="02c4b-111">たとえば、`Public`クラスは継承できません、`Friend`または`Private`クラス、および`Friend`クラスは継承できません、`Private`クラスです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="02c4b-112">継承の修飾子</span><span class="sxs-lookup"><span data-stu-id="02c4b-112">Inheritance Modifiers</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="02c4b-113">次のクラス レベルのステートメントおよび継承をサポートする修飾子が導入されています。</span><span class="sxs-lookup"><span data-stu-id="02c4b-113"> introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
-   <span data-ttu-id="02c4b-114">`Inherits`ステートメント: 基本クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-114">`Inherits` statement — Specifies the base class.</span></span>  
  
-   <span data-ttu-id="02c4b-115">`NotInheritable`修飾子、プログラマがクラスの基底クラスとして使用することを防止します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
-   <span data-ttu-id="02c4b-116">`MustInherit`修飾子: ことクラスは、基底クラスとしてのみ使用するものを指定します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="02c4b-117">インスタンスを`MustInherit`クラスを直接作成することはできません。 派生クラスの基本クラスのインスタンス作成できるだけです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="02c4b-118">(C++ や c# など他のプログラミング言語の用語が使用され*抽象クラス*をこのようなクラスを記述します)。</span><span class="sxs-lookup"><span data-stu-id="02c4b-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="02c4b-119">派生クラスのプロパティとメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="02c4b-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="02c4b-120">既定では、派生クラスは基底クラスのプロパティとメソッドを継承します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="02c4b-121">ある場合、継承されたプロパティまたはメソッドが派生クラスで動作を変えるがある*オーバーライド*します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="02c4b-122">つまり、派生クラスでメソッドの新しい実装を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="02c4b-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="02c4b-123">プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
-   <span data-ttu-id="02c4b-124">`Overridable`-派生クラスでオーバーライドするクラスでプロパティまたはメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
-   <span data-ttu-id="02c4b-125">`Overrides`— オーバーライド、`Overridable`プロパティまたはメソッドの基本クラスで定義します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
-   <span data-ttu-id="02c4b-126">`NotOverridable`-プロパティまたはメソッドの継承クラスでオーバーライドを禁止します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="02c4b-127">既定では、`Public`メソッドは、`NotOverridable`です。</span><span class="sxs-lookup"><span data-stu-id="02c4b-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
-   <span data-ttu-id="02c4b-128">`MustOverride`派生クラスでプロパティまたはメソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02c4b-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="02c4b-129">ときに、`MustOverride`キーワードを使用すると、メソッドの定義から成るだけ`Sub`、 `Function`、または`Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="02c4b-130">その他のステートメントは許可されませんし、具体的にはない`End Sub`または`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="02c4b-131">`MustOverride`メソッドを宣言する必要があります`MustInherit`クラスです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="02c4b-132">給与支払いを処理するクラスを定義するとします。</span><span class="sxs-lookup"><span data-stu-id="02c4b-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="02c4b-133">ジェネリック型を定義することが`Payroll`を含むクラス、`RunPayroll`典型的な&1; 週間の給与を計算する方法です。</span><span class="sxs-lookup"><span data-stu-id="02c4b-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="02c4b-134">使用して`Payroll`より特化されたの基本クラスとして`BonusPayroll`従業員のボーナスを配布するときに使用できるクラスです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="02c4b-135">`BonusPayroll`クラスが継承、および、上書き、`PayEmployee`ベースで定義されているメソッド`Payroll`クラスです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="02c4b-136">次の例は、基本クラスを定義`Payroll,`と派生クラスでは、 `BonusPayroll`、継承されたメソッドをオーバーライド`PayEmployee`します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="02c4b-137">プロシージャ、`RunPayroll`を作成し、渡します、`Payroll`オブジェクトと`BonusPayroll`関数の場合、オブジェクト`Pay`を実行する、`PayEmployee`両方のオブジェクトのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 <span data-ttu-id="02c4b-138">[!code-vb[VbVbalrOOP #&28;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="02c4b-138">[!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]</span></span>  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="02c4b-139">MyBase キーワード</span><span class="sxs-lookup"><span data-stu-id="02c4b-139">The MyBase Keyword</span></span>  
 <span data-ttu-id="02c4b-140">`MyBase`キーワードはクラスの現在のインスタンスの基底クラスを参照するオブジェクト変数のように動作します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-140">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="02c4b-141">`MyBase`オーバーライドまたは派生クラスでシャドウされている基本クラスのメンバーにアクセスする頻繁に使用します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-141">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="02c4b-142">具体的には、`MyBase.New`を派生クラスのコンス トラクターから基本クラス コンス トラクターを明示的に呼び出すために使用します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-142">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="02c4b-143">たとえば、基本クラスから継承されたメソッドをオーバーライドする派生クラスをデザインするとします。</span><span class="sxs-lookup"><span data-stu-id="02c4b-143">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="02c4b-144">オーバーライドされたメソッドは、基本クラスのメソッドを呼び出すおよび次のコード フラグメントで示すように、戻り値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="02c4b-144">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 <span data-ttu-id="02c4b-145">[!code-vb[VbVbalrOOP #&109;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="02c4b-145">[!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]</span></span>  
  
 <span data-ttu-id="02c4b-146">次のリストの使用に関する制限を説明する`MyBase`:</span><span class="sxs-lookup"><span data-stu-id="02c4b-146">The following list describes restrictions on using `MyBase`:</span></span>  
  
-   <span data-ttu-id="02c4b-147">`MyBase`直接の基本クラスとその継承されたメンバーを参照します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-147">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="02c4b-148">使用することはできませんにアクセスする`Private`クラスのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-148">It cannot be used to access `Private` members in the class.</span></span>  
  
-   <span data-ttu-id="02c4b-149">`MyBase`実際のオブジェクトではなく、キーワードとなります。</span><span class="sxs-lookup"><span data-stu-id="02c4b-149">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="02c4b-150">`MyBase`変数に割り当てられている、プロシージャに渡されるまたはで使用されることはできません、`Is`比較します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-150">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="02c4b-151">メソッドを`MyBase`が適用される直接の基本クラスで定義する必要はありません、間接的に継承された基本クラスで定義することがあります。</span><span class="sxs-lookup"><span data-stu-id="02c4b-151">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="02c4b-152">修飾された参照の順序で`MyBase`正しくコンパイルするため、いくつかの基本クラスが、呼び出しに使用されるパラメーターの型と名前に一致するメソッドを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="02c4b-152">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
-   <span data-ttu-id="02c4b-153">使用することはできません`MyBase`を呼び出す`MustOverride`基本クラスのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-153">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
-   <span data-ttu-id="02c4b-154">`MyBase`それ自体を修飾するために使用できません。</span><span class="sxs-lookup"><span data-stu-id="02c4b-154">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="02c4b-155">したがって、次のコードは有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="02c4b-155">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   <span data-ttu-id="02c4b-156">`MyBase`モジュールでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="02c4b-156">`MyBase` cannot be used in modules.</span></span>  
  
-   <span data-ttu-id="02c4b-157">`MyBase`としてマークされている基本クラスのメンバーにアクセスするために使用できない`Friend`基本クラスが別のアセンブリ内にある場合。</span><span class="sxs-lookup"><span data-stu-id="02c4b-157">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="02c4b-158">別の例と詳細については、次を参照してください。[方法: 派生クラスによって非表示変数にアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-158">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="02c4b-159">MyClass キーワード</span><span class="sxs-lookup"><span data-stu-id="02c4b-159">The MyClass Keyword</span></span>  
 <span data-ttu-id="02c4b-160">`MyClass`キーワードが最初に実装されているクラスの現在のインスタンスを参照するオブジェクト変数のように動作します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-160">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="02c4b-161">`MyClass`ようになります`Me`ですべてのメソッドおよびプロパティを呼び出すが、`MyClass`メソッドまたはプロパティが場合と同様に扱われる[NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-161">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="02c4b-162">そのため、メソッドまたはプロパティは左右されない派生クラスでオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="02c4b-162">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
-   <span data-ttu-id="02c4b-163">`MyClass`実際のオブジェクトではなく、キーワードとなります。</span><span class="sxs-lookup"><span data-stu-id="02c4b-163">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="02c4b-164">`MyClass`変数に割り当てられている、プロシージャに渡されるまたはで使用されることはできません、`Is`比較します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-164">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="02c4b-165">`MyClass`外側のクラスとその継承されたメンバーを参照します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-165">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
-   <span data-ttu-id="02c4b-166">`MyClass`修飾子として使用できる`Shared`メンバーです。</span><span class="sxs-lookup"><span data-stu-id="02c4b-166">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
-   <span data-ttu-id="02c4b-167">`MyClass`内で使用できません、`Shared`メソッドがインスタンス メソッドの内部クラスの共有メンバーにアクセスするのに使用できます。</span><span class="sxs-lookup"><span data-stu-id="02c4b-167">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
-   <span data-ttu-id="02c4b-168">`MyClass`標準的なモジュールでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="02c4b-168">`MyClass` cannot be used in standard modules.</span></span>  
  
-   <span data-ttu-id="02c4b-169">`MyClass`基本クラスで定義されていると、そのクラスで提供されるメソッドの実装を持たないメソッドを修飾するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="02c4b-169">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="02c4b-170">このような参照と同じ意味を持つ`MyBase.`*メソッド*します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-170">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="02c4b-171">次の例を比較`Me`と`MyClass`です。</span><span class="sxs-lookup"><span data-stu-id="02c4b-171">The following example compares `Me` and `MyClass`.</span></span>  
  
```vb
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="02c4b-172">にもかかわらず`derivedClass`オーバーライド`testMethod`、`MyClass`キーワード`useMyClass`オーバーライド、およびコンパイラの解決の効果の基底クラスのバージョンへの呼び出しを無効`testMethod`します。</span><span class="sxs-lookup"><span data-stu-id="02c4b-172">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c4b-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="02c4b-173">See Also</span></span>  
 <span data-ttu-id="02c4b-174">[Inherits ステートメント](../../../../visual-basic/language-reference/statements/inherits-statement.md) </span><span class="sxs-lookup"><span data-stu-id="02c4b-174">[Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md) </span></span>  
<span data-ttu-id="02c4b-175"> [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="02c4b-175"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>

