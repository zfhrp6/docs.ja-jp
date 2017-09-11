---
title: "クラスの定義 (Visual Basic) |Microsoft ドキュメント"
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
- execution, ending
- objects [Visual Basic], initializing
- Initialize event
- files, closing
- programs, quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event
- execution, stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
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
ms.openlocfilehash: 5b470b8ba9b60dfb1cd1bbb207e02217f5311c27
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="f41c7-102">チュートリアル: クラスの定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f41c7-102">Walkthrough: Defining Classes (Visual Basic)</span></span>
<span data-ttu-id="f41c7-103">このチュートリアルでは、オブジェクトの作成に使用することができますし、クラスを定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="f41c7-104">また、新しいクラスにプロパティとメソッドを追加する方法を説明し、オブジェクトを初期化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-a-class"></a><span data-ttu-id="f41c7-105">クラスを定義するには</span><span class="sxs-lookup"><span data-stu-id="f41c7-105">To define a class</span></span>  
  
1.  <span data-ttu-id="f41c7-106">クリックして、プロジェクトを作成**新しいプロジェクト**上、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="f41c7-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="f41c7-107">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f41c7-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="f41c7-108">一覧から Windows アプリケーションを選択[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクト テンプレートを新しいプロジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-108">Select Windows Application from the list of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="f41c7-109">クリックして新しいクラスをプロジェクトに追加**クラスの追加**上、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="f41c7-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="f41c7-110">**新しい項目の追加** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f41c7-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="f41c7-111">選択、**クラス**テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="f41c7-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="f41c7-112">新しいクラスの名前を`UserNameInfo.vb`、 をクリックし、**追加**新しいクラスのコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     <span data-ttu-id="f41c7-113">[!code-vb[VbVbalrOOP&#5;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f41c7-113">[!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f41c7-114">使用することができます、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **コード エディター** 」と入力してクラスをスタートアップ フォームに追加する、`Class`キーワードの後に、新しいクラスの名前。</span><span class="sxs-lookup"><span data-stu-id="f41c7-114">You can use the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="f41c7-115">**コード エディター** 、対応する説明`End Class`するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="f41c7-115">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="f41c7-116">間に次のコードを追加することで、クラスのプライベート フィールドを定義、`Class`と`End Class`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="f41c7-116">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     <span data-ttu-id="f41c7-117">[!code-vb[VbVbalrOOP&#7;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f41c7-117">[!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]</span></span>  
  
     <span data-ttu-id="f41c7-118">ものとしてフィールドを宣言する`Private`クラス内でのみ使用できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-118">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="f41c7-119">利用できるフィールドからクラスの外部でなどのアクセス修飾子を使用して、`Public`以上のアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-119">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="f41c7-120">詳細については、次を参照してください。 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-120">For more information, see [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="f41c7-121">次のコードを追加することで、クラスのプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-121">Define a property for the class by adding the following code:</span></span>  
  
     <span data-ttu-id="f41c7-122">[!code-vb[VbVbalrOOP&#8;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f41c7-122">[!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]</span></span>  
  
8.  <span data-ttu-id="f41c7-123">次のコードを追加することで、クラスのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-123">Define a method for the class by adding the following code:</span></span>  
  
     <span data-ttu-id="f41c7-124">[!code-vb[VbVbalrOOP&#9;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="f41c7-124">[!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]</span></span>  
  
9. <span data-ttu-id="f41c7-125">という名前のプロシージャを追加することで、新しいクラスにパラメーター化されたコンス トラクターを定義`Sub New`:</span><span class="sxs-lookup"><span data-stu-id="f41c7-125">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     <span data-ttu-id="f41c7-126">[!code-vb[VbVbalrOOP&#10;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="f41c7-126">[!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]</span></span>  
  
     <span data-ttu-id="f41c7-127">`Sub New`コンス トラクターはこのクラスに基づくオブジェクトの作成時に自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f41c7-127">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="f41c7-128">このコンス トラクターは、ユーザー名を保持するフィールドの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-128">This constructor sets the value of the field that holds the user name.</span></span>  
  
### <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="f41c7-129">クラスをテストするためのボタンを作成するには</span><span class="sxs-lookup"><span data-stu-id="f41c7-129">To create a button to test the class</span></span>  
  
1.  <span data-ttu-id="f41c7-130">その名前を右クリックして、スタートアップ フォームをデザイン モードに変更**ソリューション エクスプ ローラー**クリックし、**ビュー デザイナー**します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-130">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="f41c7-131">既定では、Windows アプリケーション プロジェクトのスタートアップ フォームを Form1.vb と呼びます。</span><span class="sxs-lookup"><span data-stu-id="f41c7-131">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="f41c7-132">メイン フォームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f41c7-132">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="f41c7-133">メイン フォームにボタンを追加し、ダブルクリックのコードを表示して、`Button1_Click`イベント ハンドラーです。</span><span class="sxs-lookup"><span data-stu-id="f41c7-133">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="f41c7-134">テストのプロシージャを呼び出すには、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-134">Add the following code to call the test procedure:</span></span>  
  
     <span data-ttu-id="f41c7-135">[!code-vb[VbVbalrOOP&#12;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="f41c7-135">[!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]</span></span>  
  
### <a name="to-run-your-application"></a><span data-ttu-id="f41c7-136">アプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="f41c7-136">To run your application</span></span>  
  
1.  <span data-ttu-id="f41c7-137">F5 キーを押して、アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="f41c7-137">Run your application by pressing F5.</span></span> <span data-ttu-id="f41c7-138">テスト プロシージャを呼び出すためのフォーム上のボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f41c7-138">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="f41c7-139">元のことを示すメッセージが表示`UserName`"MOORE、BOBBY"は、プロシージャが呼び出されるため、`Capitalize`オブジェクトのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="f41c7-139">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="f41c7-140">クリックして**OK**メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f41c7-140">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="f41c7-141">`Button1 Click`の値を変更する手順、`UserName`プロパティの新しい値のことを示すメッセージを表示および`UserName`"Worden、Joe"は、です。</span><span class="sxs-lookup"><span data-stu-id="f41c7-141">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f41c7-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="f41c7-142">See Also</span></span>  
 <span data-ttu-id="f41c7-143">[オブジェクト指向プログラミング](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2) </span><span class="sxs-lookup"><span data-stu-id="f41c7-143">[Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2) </span></span>  
<span data-ttu-id="f41c7-144"> [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="f41c7-144"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>

