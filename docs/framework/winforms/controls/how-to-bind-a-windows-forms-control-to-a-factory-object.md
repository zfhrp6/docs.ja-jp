---
title: '方法 : Windows フォーム コントロールをファクトリ オブジェクトにバインドする'
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
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c489227d12afd5e6d63a43c752ea97f06aa974e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="2ca3b-102">方法 : Windows フォーム コントロールをファクトリ オブジェクトにバインドする</span><span class="sxs-lookup"><span data-stu-id="2ca3b-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="2ca3b-103">データをやり取りするコントロールを作成している際に、他のオブジェクトを生成するオブジェクトやメソッドにコントロールをバインドすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="2ca3b-104">このようなオブジェクトやメソッドは、ファクトリと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="2ca3b-105">たとえば、データ ソースがメモリまたは型内のオブジェクトではなく、メソッドの呼び出しからの戻り値の場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="2ca3b-106">ソースがコレクションを返す限り、コントロールをこの種類のデータ ソースにバインドできます。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="2ca3b-107"><xref:System.Windows.Forms.BindingSource> コントロールを使用して、コントロールをファクトリ オブジェクトに簡単にバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ca3b-108">例</span><span class="sxs-lookup"><span data-stu-id="2ca3b-108">Example</span></span>  
 <span data-ttu-id="2ca3b-109">次の例では、<xref:System.Windows.Forms.BindingSource> コントロールを使用して、<xref:System.Windows.Forms.DataGridView> コントロールをファクトリ メソッドにバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="2ca3b-110">ファクトリ メソッドの名前は `GetOrdersByCustomerId` であり、Northwind データベースで、特定の顧客のすべての注文を返します。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ca3b-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2ca3b-111">Compiling the Code</span></span>  
 <span data-ttu-id="2ca3b-112">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-112">This example requires:</span></span>  
  
-   <span data-ttu-id="2ca3b-113">System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2ca3b-114">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2ca3b-115">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="2ca3b-116">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ca3b-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca3b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ca3b-117">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="2ca3b-118">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2ca3b-118">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="2ca3b-119">方法: Windows フォーム コントロールを型にバインドする</span><span class="sxs-lookup"><span data-stu-id="2ca3b-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
