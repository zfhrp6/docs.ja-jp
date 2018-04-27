---
title: 作成と実装インターフェイス (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0368207e0bda6e0e003ecd7988b77d765c7edc37
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="2b0e6-102">チュートリアル: インターフェイスの作成と実装 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b0e6-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="2b0e6-103">インターフェイスは、プロパティ、メソッド、およびイベントの特性を記述が最大構造体またはクラスの実装の詳細のままにします。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="2b0e6-104">このチュートリアルでは、宣言およびインターフェイスを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b0e6-105">このチュートリアルでは、ユーザー インターフェイスを作成する方法に関する情報を提供しません。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="2b0e6-106">インターフェイスを定義するには</span><span class="sxs-lookup"><span data-stu-id="2b0e6-106">To define an interface</span></span>
  
1.  <span data-ttu-id="2b0e6-107">新しい Visual Basic Windows アプリケーション プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="2b0e6-108">クリックして、プロジェクトに新しいモジュールを追加**モジュールの追加**上、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="2b0e6-109">新しいモジュールの名前を付けます`Module1.vb` をクリック**追加**です。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="2b0e6-110">新しいモジュールのコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="2b0e6-111">という名前のインターフェイスを定義する`TestInterface`内`Module1`」と入力して`Interface TestInterface`間、`Module`と`End Module`ステートメント、および ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="2b0e6-112">**コード エディター**インデント、`Interface`キーワードを追加し、`End Interface`コード ブロックを形成するステートメント。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="2b0e6-113">間に次のコードを配置することで、プロパティ、メソッド、およびインターフェイスのイベントを定義、`Interface`と`End Interface`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="2b0e6-114">実装</span><span class="sxs-lookup"><span data-stu-id="2b0e6-114">Implementation</span></span>

 <span data-ttu-id="2b0e6-115">インターフェイス メンバーを宣言するために使用する構文はクラス メンバーを宣言するための構文を異なることに注意してください可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="2b0e6-116">この違いは、インターフェイスが実装コードを含むことができないという事実を反映します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="2b0e6-117">インターフェイスを実装するには</span><span class="sxs-lookup"><span data-stu-id="2b0e6-117">To implement the interface</span></span>
  
1.  <span data-ttu-id="2b0e6-118">という名前のクラスを追加`ImplementationClass`に次のステートメントを追加することによって`Module1`の後に、`End Interface`ステートメント前に、`End Module`ステートメント、および ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="2b0e6-119">統合開発環境で作業している場合、**コード エディター**に対応する提供`End Class`ステートメント ENTER キーを押す。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="2b0e6-120">次の追加`Implements`ステートメントを`ImplementationClass`、名前、インターフェイス、クラスを実装します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="2b0e6-121">クラスまたは構造の上部にある他の項目とは別に表示されている場合、`Implements`ステートメントでは、クラスまたは構造体がインターフェイスを実装することを示します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="2b0e6-122">統合開発環境で作業している場合、**コード エディター**で必要なクラス メンバーを実装して`TestInterface`、ENTER キーを押すし、次の手順をスキップすることができます。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="2b0e6-123">統合開発環境で作業していない場合は、インターフェイスのすべてのメンバーを実装する必要があります`MyInterface`です。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="2b0e6-124">次のコードを追加`ImplementationClass`を実装する`Event1`、 `Method1`、および`Prop1`:</span><span class="sxs-lookup"><span data-stu-id="2b0e6-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="2b0e6-125">`Implements`ステートメント インターフェイスおよび実装するインターフェイス メンバーの名前します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="2b0e6-126">定義を完了`Prop1`プロパティ値を格納するクラスにプライベート フィールドを追加することで。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="2b0e6-127">値を返す、`pval`プロパティ アクセサーを取得します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="2b0e6-128">値を設定`pval`プロパティでアクセサーを設定します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5.  <span data-ttu-id="2b0e6-129">定義を完了`Method1`次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="2b0e6-130">インターフェイスの実装をテストするには</span><span class="sxs-lookup"><span data-stu-id="2b0e6-130">To test the implementation of the interface</span></span>
  
1.  <span data-ttu-id="2b0e6-131">プロジェクトをスタートアップ フォームを右クリックし、**ソリューション エクスプ ローラー**、 をクリック**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="2b0e6-132">エディターには、スタートアップ フォームのクラスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="2b0e6-133">既定では、スタートアップ フォームと呼ばれる`Form1`です。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-133">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="2b0e6-134">次の追加`testInstance`フィールドを`Form1`クラス。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="2b0e6-135">宣言することによって`testInstance`として`WithEvents`、`Form1`クラスは、そのイベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="2b0e6-136">次のイベント ハンドラーを追加、`Form1`クラスによって生成されるイベントを処理する`testInstance`:</span><span class="sxs-lookup"><span data-stu-id="2b0e6-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4.  <span data-ttu-id="2b0e6-137">という名前のサブルーチンを追加`Test`を`Form1`実装クラスをテストするクラス。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="2b0e6-138">`Test`プロシージャを実装するクラスのインスタンスの作成`MyInterface`、そのインスタンスに割り当てます、`testInstance`フィールド、プロパティの設定し、インターフェイス メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="2b0e6-139">呼び出すコードを追加、`Test`プロシージャから、`Form1 Load`スタートアップ フォームの手順。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6.  <span data-ttu-id="2b0e6-140">実行、 `Test` f5 キーを押してプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="2b0e6-141">メッセージ「Prop1 に設定された 9」が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="2b0e6-142">クリックした後、メッセージ"Method1 の X パラメーターは、5 を is"が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="2b0e6-143">[Ok]、をクリックし、「イベント ハンドラーが、イベントが発生しました」メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b0e6-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b0e6-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b0e6-144">See also</span></span>

 [<span data-ttu-id="2b0e6-145">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="2b0e6-145">Implements Statement</span></span>](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="2b0e6-146">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b0e6-146">Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [<span data-ttu-id="2b0e6-147">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="2b0e6-147">Interface Statement</span></span>](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="2b0e6-148">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="2b0e6-148">Event Statement</span></span>](../../../../visual-basic/language-reference/statements/event-statement.md)  