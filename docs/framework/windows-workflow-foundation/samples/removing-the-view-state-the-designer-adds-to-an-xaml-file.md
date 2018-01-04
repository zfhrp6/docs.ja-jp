---
title: "デザイナーによって XAML ファイルに追加されるビューステートの削除"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5da4423b5f6106bde106de739a8a33e351d17c3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="b61b4-102">デザイナーによって XAML ファイルに追加されるビューステートの削除</span><span class="sxs-lookup"><span data-stu-id="b61b4-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="b61b4-103">このサンプルでは、<xref:System.Windows.Markup.XamlWriter> から派生するクラスを作成する方法を示し、XAML ファイルからビュー ステートを削除します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]<span data-ttu-id="b61b4-104"> は、ビュー ステートと呼ばれる情報を XAML ドキュメントに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="b61b4-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="b61b4-105">ビュー ステートは、ランタイムでは不必要なレイアウト配置などの、デザイン時に必要な情報を参照します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="b61b4-106"> は、編集時に、XAML ドキュメントにこの情報を挿入します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="b61b4-107"> は、`mc:Ignorable` 属性を持つ XAML ファイルにビュー ステートを書き込みます。この結果、ランタイムが XAML ファイルを読み込みとき、この情報は読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="b61b4-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="b61b4-108">このサンプルでは、XAML ノードの処理中にそのビューステート情報を削除するクラスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b61b4-109">説明</span><span class="sxs-lookup"><span data-stu-id="b61b4-109">Discussion</span></span>  
 <span data-ttu-id="b61b4-110">このサンプルでは、カスタム ライターを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-110">This sample demonstrates how to create a custom writer.</span></span>  
  
 <span data-ttu-id="b61b4-111">カスタム XAML ライターをビルドするには、<xref:System.Windows.Markup.XamlWriter> を継承するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="b61b4-112">XAML ライターは多くの場合、入れ子になっていることが、「内部」XAML ライターを追跡する一般的なです。</span><span class="sxs-lookup"><span data-stu-id="b61b4-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="b61b4-113">これは、"内部 ' ライターはようなものの処理をスタックの残りの部分を処理を委任し、実行する複数のエントリ ポイントがあることができる XAML ライターの残りのスタックへの参照。</span><span class="sxs-lookup"><span data-stu-id="b61b4-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>  
  
 <span data-ttu-id="b61b4-114">このサンプルには、重要な項目がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="b61b4-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="b61b4-115">その 1 つとして、書き込まれる項目がデザイナー名前空間からのものであるかどうかの確認が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="b61b4-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="b61b4-116">これにより、ワークフローでデザイナー名前空間の他の型の使用が排除されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b61b4-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>  
  
```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)  
{  
    return xamlMember.IsAttachable &&  
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);  
}  
  
const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";  

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.  
public ViewStateCleaningWriter(XamlWriter innerWriter)  
{  
    this.InnerWriter = innerWriter;  
    this.MemberStack = new Stack<XamlMember>();  
}  
  
XamlWriter InnerWriter {get; set; }  
Stack<XamlMember> MemberStack {get; set; }  
```  
  
 <span data-ttu-id="b61b4-117">これにより、ノード ストリームの走査中に使用される XAML メンバーのスタックも作成されます。</span><span class="sxs-lookup"><span data-stu-id="b61b4-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="b61b4-118">このサンプルの残りの作業は主に含まれている、 <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b61b4-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>  
  
```csharp
public override void WriteStartMember(XamlMember xamlMember)  
{  
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))  
    {  
        m_attachedPropertyDepth++;  
    }  
  
    if (m_attachedPropertyDepth > 0)  
    {  
        return;  
    }  
  
    InnerWriter.WriteStartMember(xamlMember);  
}  
```  
  
 <span data-ttu-id="b61b4-119">後続のメソッドで、まだビューステート コンテナーに含まれているかどうかがチェックされ、含まれている場合は制御が戻り、ノードはライター スタックに渡されません。</span><span class="sxs-lookup"><span data-stu-id="b61b4-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>  
  
```csharp
public override void WriteValue(Object value)  
{  
    if (m_attachedPropertyDepth > 0)  
    {  
        return;  
    }  
  
    InnerWriter.WriteValue(value);  
}  
```  
  
 <span data-ttu-id="b61b4-120">カスタム XAML ライターを使用するには、XAML ライターのスタックでまとめて連結する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b61b4-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="b61b4-121">この使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-121">The following code shows how this can be used.</span></span>  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b61b4-122">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="b61b4-122">To use this sample</span></span>  
  
1. <span data-ttu-id="b61b4-123">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ViewStateCleaningWriter.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="b61b4-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ViewStateCleaningWriter.sln solution file.</span></span>  
  
2. <span data-ttu-id="b61b4-124">コマンド プロンプトを開き、ViewStageCleaningWriter.exe がビルドされているディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>  
  
3. <span data-ttu-id="b61b4-125">Workflow1.xaml ファイルに対して ViewStateCleaningWriter.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>  

   <span data-ttu-id="b61b4-126">実行可能ファイルの構文の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-126">The syntax for the executable is shown in the following example.</span></span>  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   <span data-ttu-id="b61b4-127">これにより、XAML ファイルに、出力\[出力ファイル]、削除されたすべてのビュー状態情報を持ちます。</span><span class="sxs-lookup"><span data-stu-id="b61b4-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b61b4-128"><xref:System.Activities.Statements.Sequence> ワークフローでは、多数の仮想化のヒントが削除されます。</span><span class="sxs-lookup"><span data-stu-id="b61b4-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="b61b4-129">その結果、デザイナーは次回の読み込み時にレイアウトを再計算します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="b61b4-130">このサンプルを <xref:System.Activities.Statements.Flowchart> に対して使用すると、すべての配置情報および線のルーティング情報が削除され、後続のデザイナーへの読み込み時にすべてのアクティビティが画面の左側に積み上げられます。</span><span class="sxs-lookup"><span data-stu-id="b61b4-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="b61b4-131">このサンプルで使用するサンプル XAML ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="b61b4-131">To create a sample XAML file for use with this sample</span></span>  
  
1. <span data-ttu-id="b61b4-132">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="b61b4-132">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2. <span data-ttu-id="b61b4-133">新しいワークフロー コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-133">Create a new Workflow Console Application.</span></span>  
  
3. <span data-ttu-id="b61b4-134">いくつかのアクティビティをキャンバスにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="b61b4-134">Drag and drop a few activities onto the canvas</span></span>  
  
4. <span data-ttu-id="b61b4-135">ワークフロー XAML ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-135">Save the workflow XAML file.</span></span>  
  
5. <span data-ttu-id="b61b4-136">XAML ファイルを調べて、ビューステートの添付プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="b61b4-136">Inspect the XAML file to see the view state attached properties.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b61b4-137">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b61b4-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b61b4-138">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b61b4-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b61b4-139">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="b61b4-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b61b4-140">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b61b4-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
