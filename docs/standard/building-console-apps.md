---
title: ".NET Framework におけるコンソール アプリケーションの構築"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8bcfa7d8a55cd2754965430db7ea6d2351892658
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="building-console-applications-in-the-net-framework"></a><span data-ttu-id="be85c-102">.NET Framework におけるコンソール アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="be85c-102">Building Console Applications in the .NET Framework</span></span>
<span data-ttu-id="be85c-103">.NET Framework のアプリケーションは、<xref:System.Console?displayProperty=nameWithType> クラスを使用して、コンソールから文字を読み取り、コンソールに文字を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="be85c-103">Applications in the .NET Framework can use the <xref:System.Console?displayProperty=nameWithType> class to read characters from and write characters to the console.</span></span> <span data-ttu-id="be85c-104">コンソールからのデータは標準入力ストリームから読み取られ、コンソールへのデータは標準出力ストリームに書き込まれ、コンソールへのエラー データは標準エラー出力ストリームに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="be85c-104">Data from the console is read from the standard input stream, data to the console is written to the standard output stream, and error data to the console is written to the standard error output stream.</span></span> <span data-ttu-id="be85c-105">これらのストリームは、アプリケーションの起動時に自動的にコンソールに関連付けられ、それぞれ <xref:System.Console.In%2A> プロパティ、<xref:System.Console.Out%2A> プロパティ、および <xref:System.Console.Error%2A> プロパティとして示されます。</span><span class="sxs-lookup"><span data-stu-id="be85c-105">These streams are automatically associated with the console when the application starts and are presented as the <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, and <xref:System.Console.Error%2A> properties, respectively.</span></span>  
  
 <span data-ttu-id="be85c-106"><xref:System.Console.In%2A?displayProperty=nameWithType> プロパティの値が <xref:System.IO.TextReader?displayProperty=nameWithType> オブジェクトであるのに対し、<xref:System.Console.Out%2A?displayProperty=nameWithType> および <xref:System.Console.Error%2A?displayProperty=nameWithType> プロパティの値は <xref:System.IO.TextWriter?displayProperty=nameWithType> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="be85c-106">The value of the <xref:System.Console.In%2A?displayProperty=nameWithType> property is a <xref:System.IO.TextReader?displayProperty=nameWithType> object, whereas the values of the <xref:System.Console.Out%2A?displayProperty=nameWithType> and <xref:System.Console.Error%2A?displayProperty=nameWithType> properties are <xref:System.IO.TextWriter?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="be85c-107">これらのプロパティを、コンソールを表さないストリームに関連付けることがができます。これにより、ストリームの出力先または入力元として異なる位置を指定できます。</span><span class="sxs-lookup"><span data-stu-id="be85c-107">You can associate these properties with streams that do not represent the console, making it possible for you to point the stream to a different location for input or output.</span></span> <span data-ttu-id="be85c-108">たとえば、<xref:System.Console.Out%2A?displayProperty=nameWithType> プロパティを <xref:System.Console.SetOut%2A?displayProperty=nameWithType> メソッドで <xref:System.IO.FileStream?displayProperty=nameWithType> をカプセル化する <xref:System.IO.StreamWriter?displayProperty=nameWithType> に設定することにより、出力をファイルにリダイレクトできます。</span><span class="sxs-lookup"><span data-stu-id="be85c-108">For example, you can redirect the output to a file by setting the <xref:System.Console.Out%2A?displayProperty=nameWithType> property to a <xref:System.IO.StreamWriter?displayProperty=nameWithType>, which encapsulates a <xref:System.IO.FileStream?displayProperty=nameWithType> by means of the <xref:System.Console.SetOut%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="be85c-109"><xref:System.Console.In%2A?displayProperty=nameWithType> プロパティと <xref:System.Console.Out%2A?displayProperty=nameWithType> プロパティとが同じストリームを参照する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="be85c-109">The <xref:System.Console.In%2A?displayProperty=nameWithType> and <xref:System.Console.Out%2A?displayProperty=nameWithType> properties do not need to refer to the same stream.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be85c-110">コンソール アプリケーション (C#、Visual Basic、および C++ の例を含む) をビルドする方法の詳細については <xref:System.Console> クラスのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="be85c-110">For more information about building console applications, including examples in C#, Visual Basic, and C++, see the documentation for the <xref:System.Console> class.</span></span>  
  
 <span data-ttu-id="be85c-111">Windows ベースのアプリケーションなどでコンソールが存在しない場合には、情報を書き込む先のコンソールがないため、標準出力ストリームに書き込まれた出力を参照できません。</span><span class="sxs-lookup"><span data-stu-id="be85c-111">If the console does not exist, as in a Windows-based application, output written to the standard output stream will not be visible, because there is no console to write the information to.</span></span> <span data-ttu-id="be85c-112">アクセスできないコンソールに情報を書き込んでも、例外は発生しません。</span><span class="sxs-lookup"><span data-stu-id="be85c-112">Writing information to an inaccessible console does not cause an exception to be raised.</span></span>  
  
 <span data-ttu-id="be85c-113">Visual Studio を使用して開発した Windows ベースのアプリケーション内で読み取りおよび書き込み用のコンソールを有効にするには、プロジェクトの **[プロパティ]** ダイアログ ボックスを開き、**[アプリケーション]** タブをクリックして、**[アプリケーションの種類]** を **[コンソール アプリケーション]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="be85c-113">Alternately, to enable the console for reading and writing within a Windows-based application that is developed using Visual Studio, open the project's **Properties** dialog box, click the **Application** tab, and set the **Application type** to **Console Application**.</span></span>  
  
 <span data-ttu-id="be85c-114">コンソール アプリケーションには、既定で起動されるメッセージ ポンプがありません。</span><span class="sxs-lookup"><span data-stu-id="be85c-114">Console applications lack a message pump that starts by default.</span></span> <span data-ttu-id="be85c-115">したがって、コンソールが Microsoft Win32 タイマーを呼び出すと、失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="be85c-115">Therefore, console calls to Microsoft Win32 timers might fail.</span></span>  
  
 <span data-ttu-id="be85c-116">**System.Console** クラスには、コンソールから個々の文字または行全体を読み取ることができるメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="be85c-116">The **System.Console** class has methods that can read individual characters or entire lines from the console.</span></span> <span data-ttu-id="be85c-117">その他のメソッドは、まずデータと書式指定文字列を変換してから、書式設定された文字列をコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="be85c-117">Other methods convert data and format strings, and then write the formatted strings to the console.</span></span> <span data-ttu-id="be85c-118">書式指定文字列の詳細については、「[Formatting Types](../../docs/standard/base-types/formatting-types.md)」(型の書式設定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be85c-118">For more information on formatting strings, see [Formatting Types](../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be85c-119">参照</span><span class="sxs-lookup"><span data-stu-id="be85c-119">See Also</span></span>  
 <xref:System.Console?displayProperty=nameWithType>  
 [<span data-ttu-id="be85c-120">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="be85c-120">Formatting Types</span></span>](../../docs/standard/base-types/formatting-types.md)
