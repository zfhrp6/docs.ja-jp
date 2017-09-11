---
title: "作成するインターフェイスと実装 (Visual Basic) |Microsoft ドキュメント"
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
- interfaces, walkthroughs
- interfaces, testing
- interface implementation, walkthrough
- interfaces, creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ef1ec16005bf0a7967d396054ae23c1023143c2a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="75842-102">チュートリアル: インターフェイスの作成と実装 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75842-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>
<span data-ttu-id="75842-103">インターフェイスは、プロパティ、メソッド、およびイベントの特性を記述する、最大で構造体またはクラスの実装の詳細のままです。</span><span class="sxs-lookup"><span data-stu-id="75842-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="75842-104">このチュートリアルでは、宣言およびインターフェイスを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75842-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75842-105">このチュートリアルでは、ユーザー インターフェイスを作成する方法に関する情報を提供しません。</span><span class="sxs-lookup"><span data-stu-id="75842-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-an-interface"></a><span data-ttu-id="75842-106">インターフェイスを定義するには</span><span class="sxs-lookup"><span data-stu-id="75842-106">To define an interface</span></span>  
  
1.  <span data-ttu-id="75842-107">新しい[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows アプリケーション プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="75842-107">Open a new [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="75842-108">クリックして、プロジェクトに新しいモジュールを追加**モジュールの追加**上、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="75842-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="75842-109">新しいモジュール名前`Module1.vb` をクリック**追加**します。</span><span class="sxs-lookup"><span data-stu-id="75842-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="75842-110">新しいモジュールのコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="75842-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="75842-111">という名前のインターフェイスを定義する`TestInterface`内`Module1`」と入力して`Interface TestInterface`間、`Module`と`End Module`ステートメント、および ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="75842-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="75842-112">**コード エディター**インデント、`Interface`キーワードを追加し、`End Interface`コード ブロックを形成するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="75842-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="75842-113">間に次のコードを配置することで、プロパティ、メソッド、およびインターフェイスのイベントを定義、`Interface`と`End Interface`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="75842-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     <span data-ttu-id="75842-114">[!code-vb[VbVbalrOOP #&98;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-114">[!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="75842-115">実装</span><span class="sxs-lookup"><span data-stu-id="75842-115">Implementation</span></span>  
 <span data-ttu-id="75842-116">インターフェイス メンバーの宣言に使用する構文はクラス メンバーを宣言するための構文を異なることに注意してください可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75842-116">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="75842-117">この違いは、インターフェイスが実装コードを含めることはできませんという事実を表しています。</span><span class="sxs-lookup"><span data-stu-id="75842-117">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
#### <a name="to-implement-the-interface"></a><span data-ttu-id="75842-118">インターフェイスを実装するには</span><span class="sxs-lookup"><span data-stu-id="75842-118">To implement the interface</span></span>  
  
1.  <span data-ttu-id="75842-119">という名前のクラスを追加`ImplementationClass`に次のステートメントを追加することで`Module1`後に、`End Interface`ステートメント前に、`End Module`ステートメント、および ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="75842-119">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     <span data-ttu-id="75842-120">[!code-vb[VbVbalrOOP&#99;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-120">[!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]</span></span>  
  
     <span data-ttu-id="75842-121">統合開発環境で作業している場合、**コード エディター**提供、対応する`End Class`ステートメント ENTER キーを押す。</span><span class="sxs-lookup"><span data-stu-id="75842-121">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="75842-122">次の追加`Implements`ステートメント`ImplementationClass`を実装するクラス、インターフェイスを示しています。</span><span class="sxs-lookup"><span data-stu-id="75842-122">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     <span data-ttu-id="75842-123">[!code-vb[VbVbalrOOP&#100;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-123">[!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]</span></span>  
  
     <span data-ttu-id="75842-124">クラスまたは構造の上部にある他の項目とは別に表示されている場合、`Implements`ステートメントでは、クラスまたは構造体でインターフェイスを実装することを示します。</span><span class="sxs-lookup"><span data-stu-id="75842-124">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="75842-125">統合開発環境で作業している場合、**コード エディター**で必要なクラス メンバーを実装して`TestInterface`、ENTER キーを押すし、次の手順をスキップすることができます。</span><span class="sxs-lookup"><span data-stu-id="75842-125">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="75842-126">統合開発環境で機能しない場合は、インターフェイスのすべてのメンバーを実装する必要があります`MyInterface`します。</span><span class="sxs-lookup"><span data-stu-id="75842-126">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="75842-127">次のコードを追加`ImplementationClass`を実装する`Event1`、 `Method1`、および`Prop1`:</span><span class="sxs-lookup"><span data-stu-id="75842-127">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     <span data-ttu-id="75842-128">[!code-vb[VbVbalrOOP #&101;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-128">[!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]</span></span>  
  
     <span data-ttu-id="75842-129">`Implements`ステートメント インターフェイスおよび実装するインターフェイス メンバーの名前します。</span><span class="sxs-lookup"><span data-stu-id="75842-129">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="75842-130">定義が完了`Prop1`プロパティ値を格納するクラスにプライベート フィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="75842-130">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     <span data-ttu-id="75842-131">[!code-vb[VbVbalrOOP #&102;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-131">[!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]</span></span>  
  
     <span data-ttu-id="75842-132">値を返す、`pval`プロパティ アクセサーを取得します。</span><span class="sxs-lookup"><span data-stu-id="75842-132">Return the value of the `pval` from the property get accessor.</span></span>  
  
     <span data-ttu-id="75842-133">[!code-vb[VbVbalrOOP #&103;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-133">[!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]</span></span>  
  
     <span data-ttu-id="75842-134">値を設定`pval`プロパティのアクセサーを設定します。</span><span class="sxs-lookup"><span data-stu-id="75842-134">Set the value of `pval` in the property set accessor.</span></span>  
  
     <span data-ttu-id="75842-135">[!code-vb[VbVbalrOOP #&104;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-135">[!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]</span></span>  
  
5.  <span data-ttu-id="75842-136">定義が完了`Method1`によって次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="75842-136">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     <span data-ttu-id="75842-137">[!code-vb[VbVbalrOOP #&105;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-137">[!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]</span></span>  
  
#### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="75842-138">インターフェイスの実装をテストするには</span><span class="sxs-lookup"><span data-stu-id="75842-138">To test the implementation of the interface</span></span>  
  
1.  <span data-ttu-id="75842-139">プロジェクトのスタートアップ フォームを右クリックし、**ソリューション エクスプ ローラー**、 をクリック**コードの表示**します。</span><span class="sxs-lookup"><span data-stu-id="75842-139">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="75842-140">エディターには、スタートアップ フォームのクラスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="75842-140">The editor displays the class for your startup form.</span></span> <span data-ttu-id="75842-141">既定では、スタートアップ フォームと呼ばれる`Form1`です。</span><span class="sxs-lookup"><span data-stu-id="75842-141">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="75842-142">次の追加`testInstance`フィールドを`Form1`クラス。</span><span class="sxs-lookup"><span data-stu-id="75842-142">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     <span data-ttu-id="75842-143">[!code-vb[VbVbalrOOP #&120;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-143">[!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]</span></span>  
  
     <span data-ttu-id="75842-144">宣言することで`testInstance`として`WithEvents`、`Form1`クラスは、そのイベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="75842-144">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="75842-145">次のイベント ハンドラーを追加、`Form1`クラスによって生成されるイベントを処理する`testInstance`:</span><span class="sxs-lookup"><span data-stu-id="75842-145">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     <span data-ttu-id="75842-146">[!code-vb[VbVbalrOOP #&106;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-146">[!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]</span></span>  
  
4.  <span data-ttu-id="75842-147">という名前のサブルーチンを追加`Test`に、`Form1`実装クラスをテストするクラス。</span><span class="sxs-lookup"><span data-stu-id="75842-147">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     <span data-ttu-id="75842-148">[!code-vb[VbVbalrOOP #&107;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-148">[!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]</span></span>  
  
     <span data-ttu-id="75842-149">`Test`プロシージャを実装するクラスのインスタンスの作成`MyInterface`、そのインスタンスを割り当てる、`testInstance`フィールド、プロパティの設定およびインターフェイスを通じたメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="75842-149">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="75842-150">呼び出すコードを追加、`Test`プロシージャから、`Form1 Load`スタートアップ フォームの手順。</span><span class="sxs-lookup"><span data-stu-id="75842-150">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     <span data-ttu-id="75842-151">[!code-vb[VbVbalrOOP #&108;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="75842-151">[!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]</span></span>  
  
6.  <span data-ttu-id="75842-152">実行、 `Test` f5 キーを押してプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="75842-152">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="75842-153">メッセージ「Prop1 に設定されて 9」が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75842-153">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="75842-154">クリックした後、メッセージ「Method1 の X パラメーターが 5」が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75842-154">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="75842-155">[Ok] をクリックし、「イベント ハンドラーは、イベントをキャッチ」メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="75842-155">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75842-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="75842-156">See Also</span></span>  
 <span data-ttu-id="75842-157">[Implements ステートメント](../../../../visual-basic/language-reference/statements/implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="75842-157">[Implements Statement](../../../../visual-basic/language-reference/statements/implements-statement.md) </span></span>  
<span data-ttu-id="75842-158"> [インターフェイス](../../../../visual-basic/programming-guide/language-features/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="75842-158"> [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md) </span></span>  
<span data-ttu-id="75842-159"> [Interface ステートメント](../../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="75842-159"> [Interface Statement](../../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="75842-160"> [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)</span><span class="sxs-lookup"><span data-stu-id="75842-160"> [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md)</span></span>

