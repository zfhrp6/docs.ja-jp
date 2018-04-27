---
title: '方法 : Windows フォーム BindingSource を使用した項目の追加をカスタマイズする'
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
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 400562e49b9566769f42f140f56b733954e01a0d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="bf5d8-102">方法 : Windows フォーム BindingSource を使用した項目の追加をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="bf5d8-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="bf5d8-103"><xref:System.Windows.Forms.BindingSource> コンポーネントを使用して Windows フォーム コントロールをデータ ソースにバインドする場合、新しい項目の作成のカスタマイズが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="bf5d8-104"><xref:System.Windows.Forms.BindingSource> コンポーネントでは、通常は、バインドされたコントロールで新しい項目の作成が必要になる際に発生する <xref:System.Windows.Forms.BindingSource.AddingNew> イベントが提供されるため、これが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="bf5d8-105">イベント ハンドラーは、カスタム動作が必要なものをすべて提供できます (Web サービスでのメソッドの呼び出し、クラス ファクトリからの新しいオブジェクトの取得など)。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf5d8-106"><xref:System.Windows.Forms.BindingSource.AddingNew> イベントを処理することで項目が追加された場合、追加をキャンセルすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf5d8-107">例</span><span class="sxs-lookup"><span data-stu-id="bf5d8-107">Example</span></span>  
 <span data-ttu-id="bf5d8-108">次の例では、 <xref:System.Windows.Forms.DataGridView> コンポーネントを使用して、 <xref:System.Windows.Forms.BindingSource> コントロールをクラス ファクトリにバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="bf5d8-109">ユーザーが <xref:System.Windows.Forms.DataGridView> コントロールの新しい行をクリックすると、 <xref:System.Windows.Forms.BindingSource.AddingNew> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="bf5d8-110">イベント ハンドラーは新しい `DemoCustomer` オブジェクトを作成します。これは、<xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> プロパティに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bf5d8-111">これにより、新しい `DemoCustomer` オブジェクトが <xref:System.Windows.Forms.BindingSource> コンポーネントの一覧に追加され、 <xref:System.Windows.Forms.DataGridView> コントロールの新しい行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bf5d8-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bf5d8-112">Compiling the Code</span></span>  
 <span data-ttu-id="bf5d8-113">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-113">This example requires:</span></span>  
  
-   <span data-ttu-id="bf5d8-114">System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bf5d8-115">Visual Basic または Visual c# のコマンドラインからこの例のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-115">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bf5d8-116">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="bf5d8-117">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf5d8-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5d8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf5d8-118">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="bf5d8-119">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bf5d8-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="bf5d8-120">方法: Windows フォーム コントロールを型にバインドする</span><span class="sxs-lookup"><span data-stu-id="bf5d8-120">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
