---
title: "方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9e4c1c0b432ff44af0410b1efdc3940cd0ff19c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う
Windows ストア アプリ用 .NET Framework は、完全な .NET Framework のサブセットです。 Windows ストア アプリのセキュリティおよびその他の要件のために、ファイルを開いたり読み取ったりするために使用する .NET Framework API の完全なセットを使用できません。 詳細については、 [「Windows ストア アプリ用 .NET の概要」](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)を参照してください。 ただし、他のストリームの処理操作のために .NET Framework API を使用することもできます。 これらのストリームを操作するには、 <xref:System.IO.MemoryStream> や <xref:System.IO.FileStream>などの .NET Framework ストリーム型と、 [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx)、 [IOutputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx)、 [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx)などの Windows ランタイム ストリームの間で変換が必要になる場合があります。  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` クラスには、これらの変換を簡単にするメソッドが含まれています。 ただし、.NET Framework と Windows ランタイムのストリームには、これらのメソッドの使用結果に影響する、根本的な違いがあります。 詳細については、以下のセクションで説明します。  
  
<a name="BKMK_ConvertingfromaWindowsRuntimestreamtoaNETFrameworkstream"></a>   
## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Windows ランタイム ストリームから .NET Framework ストリームへの変換  
 次の <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` メソッドのうちの 1 つを使用して、Windows ランタイム ストリームから .NET Framework ストリームに変換できます。  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream`  
 Windows ランタイムのランダムアクセス ストリームを、Windows ストア アプリ用 .NET のサブセットのマネージ ストリームに変換します。  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite`
 Windows ランタイムの出力ストリームを、Windows ストア アプリ用 .NET のサブセットのマネージ ストリームに変換します。  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead`  
 Windows ランタイムの入力ストリームを、Windows ストア アプリ用 .NET のサブセットのマネージ ストリームに変換します。  
  
 Windows ランタイムには、読み取り専用、書き込み専用、または読み取りと書き込みをサポートするストリーム型があり、これらの機能は Windows ランタイム ストリームを .NET Framework ストリームに変換した場合にも維持されます。 さらに、Windows ランタイム ストリームを .NET Framework ストリームに変換してから元に戻すと、元の Windows ランタイム インスタンスに戻ります。 変換する Windows ランタイム ストリームの機能と一致する変換メソッドを使用することをお勧めします。 ただし、 [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) は読み取りも書き込みも可能なので ( [IOutputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx) と [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx)の両方を実装しているので)、どの変換メソッドを使用しても元のストリームの機能を保持できます。 たとえば、 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead` を使用して [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) を変換すると、変換された .NET Framework ストリームは読み取りだけに制限されず、書き込みも可能になります。  
  
#### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Windows ランタイム ランダムアクセス ストリームから .NET Framework ストリームに変換するには  
  
-   <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream` メソッドを使用します。  
  
     ユーザーにファイルを選択するように要求し、Windows ランタイム API で開いて、.NET Framework のストリームに変換し、読み取ってテキスト ブロックへ出力する方法を次のコード例に示します。 このシナリオでは、通常、結果を出力する前に .NET Framework API でストリームを処理します。  
  
     この例を実行するには、 `TextBlock1` という名前のテキスト ブロックと  `Button1`という名前のボタンを含む Windows ストア XAML アプリを作成する必要があります。 ボタン クリック イベントは、例に示す `button1_Click` メソッドに関連付けられている必要があります。  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]  
  
<a name="BKMK_ConvertingfromaNETFrameworkstreamtoaWindowsRuntimestream"></a>   
## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>.NET Framework ストリームから Windows ランタイム ストリームへの変換  
 次の <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` メソッドのうちの 1 つを使用して、.NET Framework ストリームから Windows ランタイム ストリームに変換できます。  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream`  
 Windows ストア アプリ用 .NET のサブセットのマネージ ストリームを Windows ランタイムの入力ストリームに変換します。  
  
<!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A>  --> `System.IO.WindowsRuntimeStreamExtensions.AsOutputStream`
 Windows ストア アプリ用 .NET のサブセットのマネージ ストリームを、Windows ランタイムの出力ストリームに変換します。  
  
 [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md)  
 Windows ストア アプリ用 .NET のサブセットのマネージ ストリームを Windows ランタイムでの読み取りまたは書き込みに使用できるランダムアクセス ストリームに変換します。  
  
 .NET Framework ストリームを Windows ランタイム ストリームに変換する場合、変換されたストリームの機能は元のストリームによって異なります。 たとえば、元のストリームが読み取りと書き込みの両方をサポートしている場合、 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream` を呼び出してストリームを変換すると、返される型は `IRandomAccessStream`になります。この型は  `IInputStream` と `IOutputStream`を実装し、読み取りと書き込みをサポートします。  
  
 .NET Framework ストリームは、変換後も複製をサポートしません。 つまり、.NET Framework ストリームを Windows Runtime ストリームに変換し、 [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.inmemoryrandomaccessstream.getinputstreamat.aspx) を呼び出す [GetInputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.getoutputstreamat.aspx)または [GetOutputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) を呼び出すか、 [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) を直接呼び出すと、例外が発生します。  
  
#### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>.NET Framework ストリームから Windows ランタイム ランダムアクセス ストリームに変換するには  
  
-   次の例に示すように、 [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) メソッドを使用します。  
  
    > [!IMPORTANT]
    >  使用している .NET Framework ストリームがシークをサポートすること、またはそれを実行するストリームにコピーすることを確認します。 この確認には、<xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> プロパティを使用できます。  
  
     この例を実行するには、.NET Framework 4.5.1 を対象とし、 `TextBlock2` という名前のテキスト ブロックと `Button2`という名前のボタンを含む、Windows ストア XAML アプリを作成する必要があります。 ボタン クリック イベントはこの例に示す `button2_Click` メソッドに関連付けられている必要があります。  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]  
  
## <a name="see-also"></a>参照  
 [クイック スタート: ファイルの読み取りと書き込み (Windows)](http://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
 [Windows ストア アプリ用 .NET の概要](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [Windows ストア アプリ用 .NET – サポートされている API](http://msdn.microsoft.com/library/windows/apps/br230232.aspx)
