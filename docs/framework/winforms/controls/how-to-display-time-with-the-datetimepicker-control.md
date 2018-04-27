---
title: '方法 : DateTimePicker コントロールを使用して時間を表示する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cff663203e4361e4b9156ec7973c815d24c9a181
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="8a7cf-102">方法 : DateTimePicker コントロールを使用して時間を表示する</span><span class="sxs-lookup"><span data-stu-id="8a7cf-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="8a7cf-103">アプリケーションでユーザーが日付と時刻を選択して、指定された形式で日付と時刻を表示できるようにするには、<xref:System.Windows.Forms.DateTimePicker> コントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="8a7cf-104">次の手順は、<xref:System.Windows.Forms.DateTimePicker> コントロールを使用して時刻を表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="8a7cf-105">方法 : DateTimePicker コントロールを使用して時間を表示する</span><span class="sxs-lookup"><span data-stu-id="8a7cf-105">To display the time with the DateTimePicker control</span></span>  
  
1.  <span data-ttu-id="8a7cf-106"><xref:System.Windows.Forms.DateTimePicker.Format%2A> プロパティを <xref:System.Windows.Forms.DateTimePickerFormat.Time> に設定します。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="8a7cf-107"><xref:System.Windows.Forms.DateTimePicker> の <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="8a7cf-108">例</span><span class="sxs-lookup"><span data-stu-id="8a7cf-108">Example</span></span>  
 <span data-ttu-id="8a7cf-109">次のコード サンプルは、ユーザーが時刻のみを選択できるようにする <xref:System.Windows.Forms.DateTimePicker> を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a7cf-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="8a7cf-110">Compiling the Code</span></span>  
 <span data-ttu-id="8a7cf-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-111">This example requires:</span></span>  
  
-   <span data-ttu-id="8a7cf-112">System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8a7cf-113">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8a7cf-114">また、コードを新しいプロジェクトに貼り付けることにより、 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-114">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="8a7cf-115">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a7cf-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7cf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a7cf-116">See Also</span></span>  
 [<span data-ttu-id="8a7cf-117">DateTimePicker コントロール</span><span class="sxs-lookup"><span data-stu-id="8a7cf-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
