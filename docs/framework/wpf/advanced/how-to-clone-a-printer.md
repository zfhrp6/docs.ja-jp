---
title: '方法 : プリンターを複製する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
ms.openlocfilehash: 8f3a9c3b4d9f4bcbe3a6ffcff9868aa7b19b8f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="f04ca-102">方法 : プリンターを複製する</span><span class="sxs-lookup"><span data-stu-id="f04ca-102">How to: Clone a Printer</span></span>
<span data-ttu-id="f04ca-103">ほとんどの企業が、ある時点で、購入、同じモデルの複数のプリンターです。</span><span class="sxs-lookup"><span data-stu-id="f04ca-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="f04ca-104">通常、これらはすべてほぼ同一の構成の設定でインストールします。</span><span class="sxs-lookup"><span data-stu-id="f04ca-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="f04ca-105">各プリンターのインストールとできる時間がかかる場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f04ca-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="f04ca-106"><xref:System.Printing.IndexedProperties?displayProperty=nameWithType>名前空間および<xref:System.Printing.PrintServer.InstallPrintQueue%2A>Microsoft .NET Framework で公開されているクラスでは、既存の印刷キューから複製されたその他の印刷キューの任意の数を即座にインストールすることです。</span><span class="sxs-lookup"><span data-stu-id="f04ca-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with Microsoft .NET Framework makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f04ca-107">例</span><span class="sxs-lookup"><span data-stu-id="f04ca-107">Example</span></span>  
 <span data-ttu-id="f04ca-108">次の例では、2 番目の印刷キューは既存の印刷キューから複製されました。</span><span class="sxs-lookup"><span data-stu-id="f04ca-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="f04ca-109">最初の異なる 2 つ目の名前、場所、ポート、および共有状態でのみです。</span><span class="sxs-lookup"><span data-stu-id="f04ca-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="f04ca-110">これを行うための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f04ca-110">The major steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="f04ca-111">作成、<xref:System.Printing.PrintQueue>を複製する予定の既存のプリンターのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f04ca-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2.  <span data-ttu-id="f04ca-112">作成、<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>から、<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>の<xref:System.Printing.PrintQueue>です。</span><span class="sxs-lookup"><span data-stu-id="f04ca-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="f04ca-113"><xref:System.Collections.DictionaryEntry.Value%2A>このディクショナリ内の各エントリのプロパティから派生した型の 1 つのオブジェクトである<xref:System.Printing.IndexedProperties.PrintProperty>です。</span><span class="sxs-lookup"><span data-stu-id="f04ca-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="f04ca-114">これにはこのディクショナリ内のエントリの値を設定する 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="f04ca-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    -   <span data-ttu-id="f04ca-115">ディクショナリの使用**削除**と<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A>エントリを削除してから再び、目的の値に追加する方法です。</span><span class="sxs-lookup"><span data-stu-id="f04ca-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    -   <span data-ttu-id="f04ca-116">ディクショナリの使用<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f04ca-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="f04ca-117">次の例では、両方の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f04ca-117">The example below illustrates both ways.</span></span>  
  
3.  <span data-ttu-id="f04ca-118">作成、<xref:System.Printing.IndexedProperties.PrintBooleanProperty>オブジェクトし、設定、 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> 「とき」に、その<xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A>に`true`。</span><span class="sxs-lookup"><span data-stu-id="f04ca-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="f04ca-119">使用して、<xref:System.Printing.IndexedProperties.PrintBooleanProperty>オブジェクトの値を<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>の「とき」エントリです。</span><span class="sxs-lookup"><span data-stu-id="f04ca-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5.  <span data-ttu-id="f04ca-120">作成、<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトし、設定、 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "ShareName"に、その<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>に適切な<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="f04ca-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6.  <span data-ttu-id="f04ca-121">使用して、<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトの値を<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>の"ShareName"エントリです。</span><span class="sxs-lookup"><span data-stu-id="f04ca-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7.  <span data-ttu-id="f04ca-122">新しいインスタンスを作成<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトし、設定、 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "Location"とその<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>に適切な<xref:System.String>します。</span><span class="sxs-lookup"><span data-stu-id="f04ca-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8.  <span data-ttu-id="f04ca-123">もう 1 つを使用して<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトの値を<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>の「場所」のエントリ。</span><span class="sxs-lookup"><span data-stu-id="f04ca-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="f04ca-124">配列を作成する<xref:System.String>s。</span><span class="sxs-lookup"><span data-stu-id="f04ca-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="f04ca-125">各項目は、サーバー上のポートの名前です。</span><span class="sxs-lookup"><span data-stu-id="f04ca-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="f04ca-126">使用して<xref:System.Printing.PrintServer.InstallPrintQueue%2A>を新しい値で、新しいプリンターをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f04ca-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="f04ca-127">例を下回っています。</span><span class="sxs-lookup"><span data-stu-id="f04ca-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="f04ca-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f04ca-128">See Also</span></span>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="f04ca-129">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="f04ca-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="f04ca-130">印刷の概要</span><span class="sxs-lookup"><span data-stu-id="f04ca-130">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
