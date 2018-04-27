---
title: Visual Basic のオブジェクトとクラス
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 19aa20097e35a780f923a84e3e5809eb2b8bb3e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="bd500-102">Visual Basic のオブジェクトとクラス</span><span class="sxs-lookup"><span data-stu-id="bd500-102">Objects and classes in Visual Basic</span></span>
<span data-ttu-id="bd500-103">"*オブジェクト*" は、1 つの単位として扱うことができるコードとデータの組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="bd500-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="bd500-104">オブジェクトは、コントロールやフォームのように、アプリケーションの一部になることができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="bd500-105">アプリケーション全体も、オブジェクトになることができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-105">An entire application can also be an object.</span></span>

<span data-ttu-id="bd500-106">Visual Basic でアプリケーションを作成するときに常にオブジェクトを操作します。</span><span class="sxs-lookup"><span data-stu-id="bd500-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="bd500-107">コントロール、フォーム、およびデータ アクセス オブジェクトなど、Visual Basic では、によって提供されるオブジェクトを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="bd500-108">他のアプリケーションからのオブジェクトは、Visual Basic アプリケーション内でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd500-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="bd500-109">独自のオブジェクトを作成し、それらのプロパティとメソッドを追加で定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd500-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="bd500-110">オブジェクトはプログラムの作成済みの構成要素として機能し、コードを一度記述すれば、何度も再利用できます。</span><span class="sxs-lookup"><span data-stu-id="bd500-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>  
  
<span data-ttu-id="bd500-111">このトピックでは、オブジェクトの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd500-111">This topic discusses objects in detail.</span></span>  

## <a name="objects-and-classes"></a><span data-ttu-id="bd500-112">オブジェクトとクラス</span><span class="sxs-lookup"><span data-stu-id="bd500-112">Objects and classes</span></span>
<span data-ttu-id="bd500-113">Visual Basic では、各オブジェクトがによって定義された、*クラス*です。</span><span class="sxs-lookup"><span data-stu-id="bd500-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="bd500-114">クラスは、オブジェクトの変数、プロパティ、プロシージャ、およびイベントを記述します。</span><span class="sxs-lookup"><span data-stu-id="bd500-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="bd500-115">オブジェクトはクラスのインスタンスです。クラスを定義したら、必要な数のオブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="bd500-116">オブジェクトとそのクラス間の関係を理解するために、クッキーの抜き型とクッキーを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="bd500-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="bd500-117">クッキーの抜き型はクラスです。</span><span class="sxs-lookup"><span data-stu-id="bd500-117">The cookie cutter is the class.</span></span> <span data-ttu-id="bd500-118">それは、クッキーの特徴 (大きさや形など) を定義します。</span><span class="sxs-lookup"><span data-stu-id="bd500-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="bd500-119">クラスを使用して、オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="bd500-119">The class is used to create objects.</span></span> <span data-ttu-id="bd500-120">オブジェクトはクッキーです。</span><span class="sxs-lookup"><span data-stu-id="bd500-120">The objects are the cookies.</span></span>

<span data-ttu-id="bd500-121">メンバーにアクセスする前に、オブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd500-121">You must create an object before you can access its members.</span></span>  

#### <a name="to-create-an-object-from-a-class"></a><span data-ttu-id="bd500-122">クラスからオブジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="bd500-122">To create an object from a class</span></span>

1. <span data-ttu-id="bd500-123">オブジェクトの作成元となるクラスを決定します。</span><span class="sxs-lookup"><span data-stu-id="bd500-123">Determine from which class you want to create an object.</span></span>  

2. <span data-ttu-id="bd500-124">[Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)を記述して、クラス インスタンスを割り当てることができる変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="bd500-124">Write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="bd500-125">変数は、目的のクラスの型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd500-125">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As customer
   ```

3. <span data-ttu-id="bd500-126">[New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)キーワードを追加して、変数をクラスの新しいインスタンスに初期化します。</span><span class="sxs-lookup"><span data-stu-id="bd500-126">Add the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New customer
   ```

4. <span data-ttu-id="bd500-127">これで、オブジェクト変数を使用してクラスのメンバーにアクセスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bd500-127">You can now access the members of the class through the object variable.</span></span>  

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1  
   ```

> [!NOTE]
>  <span data-ttu-id="bd500-128">可能であれば、変数は、変数に割り当てる予定のクラスの型で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd500-128">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="bd500-129">これは、*事前バインディング*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="bd500-129">This is called *early binding*.</span></span> <span data-ttu-id="bd500-130">コンパイル時にクラスの型を把握していない場合は、変数を [Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)で宣言することで、*遅延バインディング*を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-130">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="bd500-131">ただし、遅延バインディングでは、パフォーマンスが低下し、実行時のオブジェクトのメンバーへのアクセスが制限される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bd500-131">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="bd500-132">詳細については、「[オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-132">For more information, see [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="bd500-133">複数インスタンス</span><span class="sxs-lookup"><span data-stu-id="bd500-133">Multiple instances</span></span>
<span data-ttu-id="bd500-134">多くの場合、クラスから新しく作成されたオブジェクトは互いに同一です。</span><span class="sxs-lookup"><span data-stu-id="bd500-134">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="bd500-135">ただし、個々のオブジェクトとして存在した後、それぞれの変数とプロパティは、他のインスタンスとは無関係に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-135">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="bd500-136">たとえば、次の 3 つのチェック ボックスをフォームに追加する場合、各チェック ボックスのオブジェクトは、<xref:System.Windows.Forms.CheckBox> クラスのインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="bd500-136">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="bd500-137">個々の <xref:System.Windows.Forms.CheckBox> オブジェクトは、クラスによって定義された特性と機能 (プロパティ、変数、プロシージャ、およびイベント) の共通セットを共有します。</span><span class="sxs-lookup"><span data-stu-id="bd500-137">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="bd500-138">ただし、それぞれが独自の名前を持ち、別々に有効または無効にすることができ、フォームの異なる場所に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-138">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="bd500-139">オブジェクトのメンバー</span><span class="sxs-lookup"><span data-stu-id="bd500-139">Object members</span></span>
<span data-ttu-id="bd500-140">オブジェクトはアプリケーションの要素であり、クラスの "*インスタンス*" を表しています。</span><span class="sxs-lookup"><span data-stu-id="bd500-140">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="bd500-141">フィールド、プロパティ、メソッド、およびイベントは、オブジェクトの構成要素であり、オブジェクトの*メンバー*を構成します。</span><span class="sxs-lookup"><span data-stu-id="bd500-141">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="bd500-142">メンバー アクセス</span><span class="sxs-lookup"><span data-stu-id="bd500-142">Member Access</span></span>
<span data-ttu-id="bd500-143">オブジェクトのメンバーにアクセスするには、オブジェクト変数の名前、ピリオド (`.`)、およびメンバーの名前をこの順序で指定します。</span><span class="sxs-lookup"><span data-stu-id="bd500-143">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="bd500-144"><xref:System.Windows.Forms.Label> オブジェクトの <xref:System.Windows.Forms.Control.Text%2A> プロパティを設定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bd500-144">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="bd500-145">メンバーの IntelliSense の一覧</span><span class="sxs-lookup"><span data-stu-id="bd500-145">IntelliSense listing of members</span></span>
<span data-ttu-id="bd500-146">IntelliSense は、[メンバーの一覧] オプションが呼び出されたとき (たとえばメンバー アクセス演算子としてピリオド (`.`) が入力されたとき) に、クラスのメンバーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="bd500-146">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="bd500-147">ピリオドに続けて、そのクラスのインスタンスとして宣言された変数の名前を入力すると、IntelliSense は、すべてのインスタンス メンバーを表示しますが、共有メンバーは表示しません。</span><span class="sxs-lookup"><span data-stu-id="bd500-147">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="bd500-148">クラス名に続けてピリオドを入力すると、IntelliSense は、すべての共有メンバーを表示し、インスタンス メンバーは表示しません。</span><span class="sxs-lookup"><span data-stu-id="bd500-148">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="bd500-149">詳細については、「[IntelliSense の使用](/visualstudio/ide/using-intellisense)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-149">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="bd500-150">フィールドとプロパティ</span><span class="sxs-lookup"><span data-stu-id="bd500-150">Fields and properties</span></span>
<span data-ttu-id="bd500-151">"*フィールド*" と "*プロパティ*" は、オブジェクトに格納されている情報を表します。</span><span class="sxs-lookup"><span data-stu-id="bd500-151">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="bd500-152">代入ステートメントによる値の取得と設定は、プロシージャでローカル変数の取得と設定を行うのと同じ方法で実行します。</span><span class="sxs-lookup"><span data-stu-id="bd500-152">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="bd500-153">次の例では <xref:System.Windows.Forms.Control.Width%2A> プロパティを取得し、<xref:System.Windows.Forms.Label> オブジェクトの <xref:System.Windows.Forms.Control.ForeColor%2A> プロパティを設定しています。</span><span class="sxs-lookup"><span data-stu-id="bd500-153">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="bd500-154">フィールドは、"*メンバー変数*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="bd500-154">Note that a field is also called a *member variable*.</span></span>
  
<span data-ttu-id="bd500-155">次の場合は、プロパティ プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd500-155">Use property procedures when:</span></span>

- <span data-ttu-id="bd500-156">値を設定または取得するタイミングと方法を制御する必要がある。</span><span class="sxs-lookup"><span data-stu-id="bd500-156">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="bd500-157">プロパティに、検証する必要がある適切に定義された一連の値がある。</span><span class="sxs-lookup"><span data-stu-id="bd500-157">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="bd500-158">値を設定することで、オブジェクトの状態をはっきりと変更する (例: `IsVisible` プロパティ)。</span><span class="sxs-lookup"><span data-stu-id="bd500-158">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="bd500-159">プロパティを設定することで、他の内部変数またはその他のプロパティの値を変更する。</span><span class="sxs-lookup"><span data-stu-id="bd500-159">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="bd500-160">プロパティを設定または取得する前に、一連の手順を実行する必要がある。</span><span class="sxs-lookup"><span data-stu-id="bd500-160">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="bd500-161">次の場合は、フィールドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd500-161">Use fields when:</span></span>  

- <span data-ttu-id="bd500-162">値は自己検証型である。</span><span class="sxs-lookup"><span data-stu-id="bd500-162">The value is of a self-validating type.</span></span> <span data-ttu-id="bd500-163">たとえば、`Boolean` 変数に `True` または `False` の値が割り当てられた場合は、エラーまたはデータの自動変換が発生します。</span><span class="sxs-lookup"><span data-stu-id="bd500-163">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="bd500-164">データ型によってサポートされている範囲の値はすべて有効である。</span><span class="sxs-lookup"><span data-stu-id="bd500-164">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="bd500-165">これは、`Single` 型または `Double` 型の多くのプロパティに当てはまります。</span><span class="sxs-lookup"><span data-stu-id="bd500-165">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="bd500-166">プロパティは `String` データ型であり、文字列のサイズまたは値に制限がない。</span><span class="sxs-lookup"><span data-stu-id="bd500-166">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="bd500-167">詳細については、「[プロパティ プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-167">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

### <a name="methods"></a><span data-ttu-id="bd500-168">メソッド</span><span class="sxs-lookup"><span data-stu-id="bd500-168">Methods</span></span>
<span data-ttu-id="bd500-169">"*メソッド*" は、オブジェクトが実行できる処理です。</span><span class="sxs-lookup"><span data-stu-id="bd500-169">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="bd500-170">たとえば、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> は、コンボ ボックスに新しいエントリを追加する <xref:System.Windows.Forms.ComboBox> オブジェクトのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="bd500-170">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="bd500-171">次の例は、<xref:System.Windows.Forms.Timer> オブジェクトの <xref:System.Windows.Forms.Timer.Start%2A> メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd500-171">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="bd500-172">メソッドは、オブジェクトによって公開される "*プロシージャ*" です。</span><span class="sxs-lookup"><span data-stu-id="bd500-172">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="bd500-173">詳細については、「[プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-173">For more information, see [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="bd500-174">イベント</span><span class="sxs-lookup"><span data-stu-id="bd500-174">Events</span></span>
<span data-ttu-id="bd500-175">イベントは、マウスのクリックやキーの押下などのオブジェクトによって認識される操作であり、それに応答するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="bd500-175">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="bd500-176">イベントは、ユーザーの操作またはプログラム コードの結果として発生する可能性がありますが、システムによって発生する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bd500-176">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="bd500-177">イベントを通知するコードを、イベントを "*発生させる*" と言い、イベントに応答するコードを、イベントを "*処理する*" と言います。</span><span class="sxs-lookup"><span data-stu-id="bd500-177">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="bd500-178">オブジェクトによって発生する独自のカスタム イベントを作成し、その他のオブジェクトで処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd500-178">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="bd500-179">詳細については、「[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-179">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="bd500-180">インスタンス メンバーと共有メンバー</span><span class="sxs-lookup"><span data-stu-id="bd500-180">Instance members and shared members</span></span>
<span data-ttu-id="bd500-181">クラスからオブジェクトを作成した結果が、そのクラスのインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="bd500-181">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="bd500-182">[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) キーワードなしで宣言されたメンバーは、"*インスタンス メンバー*" になり、特定のインスタンスにのみ属します。</span><span class="sxs-lookup"><span data-stu-id="bd500-182">Members that are not declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="bd500-183">あるインスタンスのインスタンス メンバーは、同じクラスの別のインスタンスに同じメンバーがあっても互いに独立しています。</span><span class="sxs-lookup"><span data-stu-id="bd500-183">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="bd500-184">たとえばインスタンス メンバー変数は、インスタンスごとに異なる値を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-184">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="bd500-185">`Shared` キーワード付きで宣言されたメンバーは "*共有メンバー*" になり、全体がクラスに属し、特定のインスタンスには属しません。</span><span class="sxs-lookup"><span data-stu-id="bd500-185">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="bd500-186">共有メンバーは、作成するクラスのインスタンスの数に関係なく 1 度だけ存在します。これは、インスタンスを作成していない場合でも同じです。</span><span class="sxs-lookup"><span data-stu-id="bd500-186">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="bd500-187">たとえば共有メンバー変数は、クラスにアクセスできるすべてのコードが使用できる 1 つの値のみを持っています。</span><span class="sxs-lookup"><span data-stu-id="bd500-187">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-nonshared-members"></a><span data-ttu-id="bd500-188">非共有メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="bd500-188">Accessing nonshared members</span></span>  

###### <a name="to-access-a-nonshared-member-of-an-object"></a><span data-ttu-id="bd500-189">オブジェクトの非共有メンバーにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="bd500-189">To access a nonshared member of an object</span></span>

1. <span data-ttu-id="bd500-190">オブジェクトがクラスから作成され、オブジェクト変数に割り当てられていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-190">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form  
   ```  

2. <span data-ttu-id="bd500-191">メンバーにアクセスするステートメントで、オブジェクト変数名に続けて、"*メンバー アクセス演算子"*  (`.`) とメンバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd500-191">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="bd500-192">共有メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="bd500-192">Accessing shared members</span></span>

###### <a name="to-access-a-shared-member-of-an-object"></a><span data-ttu-id="bd500-193">オブジェクトの共有メンバーにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="bd500-193">To access a shared member of an object</span></span>

- <span data-ttu-id="bd500-194">クラス名に続けて、"*メンバー アクセス演算子*" (`.`) とメンバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd500-194">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="bd500-195">オブジェクトの `Shared` メンバーは、常にクラス名から直接アクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd500-195">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)  
   ```

- <span data-ttu-id="bd500-196">既にクラスからオブジェクトを作成している場合は、オブジェクト変数を使用して `Shared` メンバーにアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bd500-196">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="bd500-197">クラスとモジュールの違い</span><span class="sxs-lookup"><span data-stu-id="bd500-197">Differences between classes and modules</span></span>
<span data-ttu-id="bd500-198">クラスとモジュールの主な違いは、クラスはオブジェクトとしてインスタンス化できますが、標準モジュールではできないことです。</span><span class="sxs-lookup"><span data-stu-id="bd500-198">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="bd500-199">標準モジュールのデータは 1 つしかないため、プログラムのある部分が標準モジュールのパブリック変数を変更した場合、その後、プログラムの他の部分がその変数を読み取ると、変更後の値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="bd500-199">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="bd500-200">これに対し、オブジェクト データは、インスタンス化されたオブジェクトごとに個別に存在します。</span><span class="sxs-lookup"><span data-stu-id="bd500-200">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="bd500-201">別の相違点は、標準モジュールとは異なり、クラスはインターフェイスを実装できることです。</span><span class="sxs-lookup"><span data-stu-id="bd500-201">Another difference is that unlike standard modules, classes can implement interfaces.</span></span>

> [!NOTE]
> <span data-ttu-id="bd500-202">`Shared` 修飾子は、クラス メンバーに適用された場合は、クラスの特定のインスタンスではなく、クラス自体に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="bd500-202">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="bd500-203">メンバーへのアクセスは、モジュール メンバーへのアクセス方法と同じように、クラス名を使用して直接行います。</span><span class="sxs-lookup"><span data-stu-id="bd500-203">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="bd500-204">さらに、クラスとモジュールは、メンバーに対して異なるスコープを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd500-204">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="bd500-205">クラス内に定義されているメンバーのスコープはクラスの特定のインスタンス内に限られ、オブジェクトの有効期間のみ存在します。</span><span class="sxs-lookup"><span data-stu-id="bd500-205">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="bd500-206">クラスの外部からクラス メンバーにアクセスするには、"*オブジェクト*.*メンバー*" 形式の完全修飾名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd500-206">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="bd500-207">その一方で、モジュール内に宣言されているメンバーは、既定ではパブリックにアクセスすることができ、モジュールにアクセスできるすべてのコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bd500-207">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="bd500-208">つまり、標準モジュール内の変数は、プロジェクト内の任意の場所から参照でき、プログラムが実行されている間は存在するため、実質的にはグローバル変数です。</span><span class="sxs-lookup"><span data-stu-id="bd500-208">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="bd500-209">クラスとオブジェクトの再利用</span><span class="sxs-lookup"><span data-stu-id="bd500-209">Reusing classes and objects</span></span>  
<span data-ttu-id="bd500-210">オブジェクトを使用すると、変数とプロシージャを 1 度宣言した後、必要に応じていつでもそれらを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="bd500-210">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="bd500-211">たとえば、スペル チェック機能をアプリケーションに追加する場合は、スペル チェック機能を提供するためのすべての変数とサポート機能を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-211">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="bd500-212">スペル チェック機能をクラスとして作成した場合は、コンパイルされたアセンブリへの参照を追加することで、他のアプリケーションで再利用できます。</span><span class="sxs-lookup"><span data-stu-id="bd500-212">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="bd500-213">さらに、誰かが既に開発したスペル チェック機能のクラスを使用することで、作業の手間を省くことができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-213">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="bd500-214">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] には、使用可能なコンポーネントの例が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="bd500-214">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provides many examples of components that are available for use.</span></span> <span data-ttu-id="bd500-215">次の例では、<xref:System> 名前空間に <xref:System.TimeZone> クラスが使用されています。</span><span class="sxs-lookup"><span data-stu-id="bd500-215">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="bd500-216"><xref:System.TimeZone> は、現在のコンピューター システムのタイム ゾーンに関する情報を取得できるメンバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="bd500-216"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

<span data-ttu-id="bd500-217">上記の例では、最初の [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)が <xref:System.TimeZone> 型のオブジェクト変数を宣言し、<xref:System.TimeZone.CurrentTimeZone%2A> プロパティによって返された <xref:System.TimeZone> オブジェクトに割り当てています。</span><span class="sxs-lookup"><span data-stu-id="bd500-217">In the preceding example, the first [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="bd500-218">オブジェクト間の関係</span><span class="sxs-lookup"><span data-stu-id="bd500-218">Relationships among objects</span></span>  
<span data-ttu-id="bd500-219">オブジェクトは、いくつかの方法で相互に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-219">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="bd500-220">リレーションシップの主要な種類は、"*階層*" と "*含有*" です。</span><span class="sxs-lookup"><span data-stu-id="bd500-220">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="bd500-221">階層関係</span><span class="sxs-lookup"><span data-stu-id="bd500-221">Hierarchical relationship</span></span>
<span data-ttu-id="bd500-222">より基礎的なクラスから派生したクラスは、"*階層関係*" があると言います。</span><span class="sxs-lookup"><span data-stu-id="bd500-222">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="bd500-223">クラスの階層は、より一般的なクラスのサブタイプである項目を記述する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="bd500-223">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="bd500-224">次の例では、通常の <xref:System.Windows.Forms.Button> と同じように機能しますが、前景と背景の色を逆転させるメソッドも公開する、特殊な <xref:System.Windows.Forms.Button> を定義します。</span><span class="sxs-lookup"><span data-stu-id="bd500-224">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a><span data-ttu-id="bd500-225">既に存在するクラスから派生するクラスを定義するのには</span><span class="sxs-lookup"><span data-stu-id="bd500-225">To define a class is derived from an already existing class</span></span>

1. <span data-ttu-id="bd500-226">[Class ステートメント](../../../../visual-basic/language-reference/statements/class-statement.md)を使用して、必要なオブジェクトの作成元となるクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="bd500-226">Use a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class reversibleButton
   ```

   <span data-ttu-id="bd500-227">クラスのコードの最後の行の後に、必ず `End Class` ステートメントを指定してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-227">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="bd500-228">統合開発環境 (IDE) では、既定により、`Class` ステートメントを入力すると、`End Class` が自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="bd500-228">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="bd500-229">`Class` ステートメントの直後に、[Inherits ステートメント](../../../../visual-basic/language-reference/statements/inherits-statement.md)を記述します。</span><span class="sxs-lookup"><span data-stu-id="bd500-229">Follow the `Class` statement immediately with an [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="bd500-230">新しいクラスの派生元クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bd500-230">Specify the class from which your new class derives.</span></span>  
  
   ```vb
   Inherits System.Windows.Forms.Button
   ```

  <span data-ttu-id="bd500-231">新しいクラスは、基本クラスによって定義されたすべてのメンバーを継承します。</span><span class="sxs-lookup"><span data-stu-id="bd500-231">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="bd500-232">派生クラスで公開される追加のメンバー用のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd500-232">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="bd500-233">たとえば、`reverseColors` メソッドを追加すると、派生クラスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bd500-233">For example, you might add a `reverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="bd500-234">`reversibleButton` クラスからオブジェクトを作成すると、オブジェクトは、<xref:System.Windows.Forms.Button> クラスのすべてのメンバーだけでなく、`reverseColors` メソッドと`reversibleButton` に定義したその他の新しいメンバーにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bd500-234">If you create an object from the `reversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `reverseColors` method and any other new members you define on `reversibleButton`.</span></span>

<span data-ttu-id="bd500-235">派生クラスは、派生元のクラスからメンバーを継承するため、クラス階層が深くなるにつれて、クラスをより複雑にすることができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-235">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="bd500-236">詳細については、「[継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-236">For more information, see [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

#### <a name="compiling-the-code"></a><span data-ttu-id="bd500-237">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bd500-237">Compiling the code</span></span>
<span data-ttu-id="bd500-238">コンパイラが、新しいクラスの派生元となるクラスにアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bd500-238">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="bd500-239">これは、上記の例のように名前を完全に修飾するか、名前空間を [Imports ステートメント (.NET 名前空間と型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) で識別することを意味する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd500-239">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="bd500-240">クラスが別のプロジェクト内にある場合は、そのプロジェクトへの参照の追加が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="bd500-240">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="bd500-241">詳細については、「[プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-241">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="bd500-242">含有リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="bd500-242">Containment relationship</span></span>
<span data-ttu-id="bd500-243">オブジェクトを関連付けることのできる別の方法は、"*含有関係*" にすることです。</span><span class="sxs-lookup"><span data-stu-id="bd500-243">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="bd500-244">コンテナー オブジェクトは、その他のオブジェクトを論理的にカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="bd500-244">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="bd500-245">たとえば、<xref:System.OperatingSystem> オブジェクトには、その <xref:System.OperatingSystem.Version%2A> プロパティによって返される <xref:System.Version> オブジェクトが論理的に含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd500-245">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="bd500-246">コンテナー オブジェクトが物理的にその他のオブジェクトを含んでいるわけではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bd500-246">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="bd500-247">コレクション</span><span class="sxs-lookup"><span data-stu-id="bd500-247">Collections</span></span>
<span data-ttu-id="bd500-248">特別な種類のオブジェクトの含有として、"*コレクション*" と表現されるものがあります。</span><span class="sxs-lookup"><span data-stu-id="bd500-248">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="bd500-249">コレクションは、列挙することができる類似のオブジェクトの集まりです。</span><span class="sxs-lookup"><span data-stu-id="bd500-249">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="bd500-250">Visual Basic で特定の構文をサポートしている、[ごとにしています.次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)コレクションの項目を反復処理することができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-250">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="bd500-251">さらに、多くの場合、コレクションでは、<xref:Microsoft.VisualBasic.Collection.Item%2A> を使用して、その要素を、インデックスまたは一意の文字列の関連付けによって取得することができます。</span><span class="sxs-lookup"><span data-stu-id="bd500-251">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="bd500-252">コレクションは、インデックスなしで項目を削除または追加できるため、配列よりも簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd500-252">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="bd500-253">簡単に使用できるため、多くの場合、コレクションは、フォームとコントロールを格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd500-253">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="bd500-254">関連トピック</span><span class="sxs-lookup"><span data-stu-id="bd500-254">Related topics</span></span>  
 [<span data-ttu-id="bd500-255">チュートリアル : クラスの定義</span><span class="sxs-lookup"><span data-stu-id="bd500-255">Walkthrough: Defining Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 <span data-ttu-id="bd500-256">クラスを作成する方法を手順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="bd500-256">Provides a step-by-step description of how to create a class.</span></span>  

 [<span data-ttu-id="bd500-257">オーバーロードされたプロパティとメソッド</span><span class="sxs-lookup"><span data-stu-id="bd500-257">Overloaded Properties and Methods</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 <span data-ttu-id="bd500-258">オーバーロードされたプロパティとメソッド</span><span class="sxs-lookup"><span data-stu-id="bd500-258">Overloaded Properties and Methods</span></span>  

 [<span data-ttu-id="bd500-259">継承の基本</span><span class="sxs-lookup"><span data-stu-id="bd500-259">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="bd500-260">継承修飾子、メソッドとプロパティのオーバーライド、MyClass、および MyBase について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd500-260">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>  

 [<span data-ttu-id="bd500-261">オブジェクトの有効期間 : オブジェクトの作成と破棄</span><span class="sxs-lookup"><span data-stu-id="bd500-261">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 <span data-ttu-id="bd500-262">クラス インスタンスの作成と破棄について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd500-262">Discusses creating and disposing of class instances.</span></span>  

 [<span data-ttu-id="bd500-263">匿名型</span><span class="sxs-lookup"><span data-stu-id="bd500-263">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 <span data-ttu-id="bd500-264">匿名型を作成して使用する方法について説明します。匿名型を使用すると、データ型のクラス定義を記述せずにオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bd500-264">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>  

 [<span data-ttu-id="bd500-265">オブジェクト初期化子 : 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="bd500-265">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 <span data-ttu-id="bd500-266">1 つの式で名前付きの型と匿名型のインスタンスを作成するために使用する、オブジェクト初期化子について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd500-266">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>  

 [<span data-ttu-id="bd500-267">方法 : 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="bd500-267">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 <span data-ttu-id="bd500-268">匿名型で宣言されたプロパティの名前と型を推論する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd500-268">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="bd500-269">推論の成功例と失敗例を示します。</span><span class="sxs-lookup"><span data-stu-id="bd500-269">Provides examples of successful and unsuccessful inference.</span></span>
