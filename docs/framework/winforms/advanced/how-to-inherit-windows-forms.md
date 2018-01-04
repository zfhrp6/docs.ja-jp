---
title: "方法 : Windows フォームを継承する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f190fb101a3ff666d194d854c9ce152657ebf85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="2ad19-102">方法 : Windows フォームを継承する</span><span class="sxs-lookup"><span data-stu-id="2ad19-102">How to: Inherit Windows Forms</span></span>
<span data-ttu-id="2ad19-103">新規の Windows フォームは、基本フォームから継承して簡単に複製できます。フォームが必要になるたびに、最初から作成し直す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2ad19-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>  
  
 <span data-ttu-id="2ad19-104">デザイン時に **[継承ピッカー]** ダイアログ ボックスを使用してフォームを継承する方法、および継承されるコントロールのセキュリティ レベルを視覚的に区別する方法の詳細については、「[方法: [継承ピッカー] ダイアログ ボックスを使用してフォームを継承する](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ad19-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>  
  
 <span data-ttu-id="2ad19-105">**メモ** フォームを継承するには、そのフォームを含むファイルまたは名前空間が実行可能ファイルまたは DLL に組み込まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ad19-105">**Note** In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="2ad19-106">プロジェクトをビルドするには、**[ビルド]** メニューの **[ビルド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ad19-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="2ad19-107">また、フォームの継承先となるクラスに、名前空間への参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ad19-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span> <span data-ttu-id="2ad19-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ad19-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2ad19-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ad19-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2ad19-110">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ad19-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-inherit-a-form-programmatically"></a><span data-ttu-id="2ad19-111">プログラムによってフォームを継承するには</span><span class="sxs-lookup"><span data-stu-id="2ad19-111">To inherit a form programmatically</span></span>  
  
1.  <span data-ttu-id="2ad19-112">クラスに、継承元のフォームを含む名前空間への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="2ad19-112">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>  
  
2.  <span data-ttu-id="2ad19-113">クラス定義に、継承元のフォームへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="2ad19-113">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="2ad19-114">参照では、フォームを含んでいる名前空間を指定し、その後にピリオド、続いて基本フォーム自体の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2ad19-114">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 <span data-ttu-id="2ad19-115">フォームを継承する場合は、イベント ハンドラーが 2 回呼び出されることで問題が発生する可能性があることに注意してください。これは、各イベントが基底クラスと継承クラスの両方によって処理されるためです。</span><span class="sxs-lookup"><span data-stu-id="2ad19-115">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="2ad19-116">この問題を回避する方法の詳細については、「[Visual Basic で継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ad19-116">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad19-117">参照</span><span class="sxs-lookup"><span data-stu-id="2ad19-117">See Also</span></span>  
 [<span data-ttu-id="2ad19-118">Inherits ステートメント</span><span class="sxs-lookup"><span data-stu-id="2ad19-118">Inherits Statement</span></span>](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="2ad19-119">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="2ad19-119">Imports Statement (.NET Namespace and Type)</span></span>](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="2ad19-120">using</span><span class="sxs-lookup"><span data-stu-id="2ad19-120">using</span></span>](~/docs/csharp/language-reference/keywords/using.md)  
 [<span data-ttu-id="2ad19-121">基本フォームの外観を変更した場合の影響</span><span class="sxs-lookup"><span data-stu-id="2ad19-121">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [<span data-ttu-id="2ad19-122">Windows フォームのビジュアルの継承</span><span class="sxs-lookup"><span data-stu-id="2ad19-122">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
