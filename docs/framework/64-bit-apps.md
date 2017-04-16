---
title: "64 ビット アプリケーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "64 ビット アプリケーション [C++]"
  - "64 ビット プログラミング [C++]"
  - "アプリケーション [C++], 64 ビット"
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
caps.latest.revision: 53
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 53
---
# 64 ビット アプリケーション
アプリケーションをコンパイルするときに、Windows 64 ビット オペレーティング システム上で、ネイティブ アプリケーションとして実行するか、WOW64 \(Windows 64 ビット上の Windows 32 ビット\) の制御下で実行するかを指定できます。  WOW64 は互換環境であり、32 ビット アプリケーションを 64 ビット オペレーティング システム上で実行できるようにします。  WOW64 は、Windows オペレーティング システムのすべての 64 ビット バージョンに含まれています。  
  
## Windows における 32 ビット アプリケーションと 64 ビット アプリケーションの実行の比較  
 .NET Framework 1.0 および 1.1 リリースでビルドされたアプリケーションはすべて、64 ビットのオペレーティング システム上の 32 ビット アプリケーションとして扱われます。そして常に、WOW64 と 32 ビットの共通言語ランタイム \(CLR: Common Language Runtime\) のもとで実行します。  [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)] 以降のバージョンでビルドされた 32 ビット アプリケーションも、64 ビット システムでは WOW64 のもとで実行します。  
  
 Visual Studio は、x86 コンピューターには 32 ビット版の CLR をインストールし、64 ビットの Windows コンピューターには、32 ビット版の CLR と適切な 64 ビット版の CLR の両方をインストールします   \(Visual Studio は 32 ビット アプリケーションであるため、64 ビット システムにインストールすると WOW64 の制御下で実行されます\)。  
  
> [!NOTE]
>  x86 エミュレーションと、Itanium プロセッサ ファミリ向け WOW64 サブシステムの設計のために、アプリケーションの実行は単一のプロセッサ上に制限されます。  これらの要因により、Itanium ベースのシステム上で実行する 32 ビット .NET Framework アプリケーションのパフォーマンスとスケーラビリティは低下します。  パフォーマンスおよびスケーラビリティを向上させるために、Itanium ベースのシステム用のネイティブ 64 ビット サポートを含む [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)] を使用することをお勧めします。  
  
 既定では、64 ビット Windows オペレーティング システムで 64 ビット マネージ アプリケーションを実行するときに、最大 2 GB のオブジェクトを作成できます。  ただし、[!INCLUDE[net_v45](../../includes/net-v45-md.md)] ではこの制限を上げることができます。  詳細については、「[\<gcAllowVeryLargeObjects\> 要素](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)」を参照してください。  
  
 多くのアセンブリは 32 ビットの CLR と 64 ビットの CLR で同じように実行します。  しかし、次の条件が当てはまる場合、一部のプログラムでは動作が CLR によって異なります。  
  
-   プラットフォームによってメンバーのサイズが変わる構造体 \(ポインター型など\)  
  
-   定数のサイズを含むポインター演算  
  
-   ハンドルに `Int32` ではなく `IntPtr` を使用した不適切なプラットフォーム呼び出しまたは COM 宣言  
  
-   `IntPtr` を `Int32` にキャストするコード  
  
 32 ビット アプリケーションを 64 ビットの CLR に移行して実行する方法の詳細については、[MSDN ライブラリの「Migrating 32\-bit Managed Code to 64\-bit](http://go.microsoft.com/fwlink/?LinkId=150542)」を参照してください。  
  
## 一般的な 64 ビット プログラミングについて  
 64 ビット プログラミングの一般的な問題については、次のドキュメントを参照してください。  
  
-   64 ビット Windows コンピューター上の 64 ビット版 CLR の詳細については、MSDN Web サイトの「[.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=37079)」を参照してください。  
  
-   [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] ドキュメントの「[64 ビット Windows プログラミング ガイド](http://go.microsoft.com/fwlink/p/?LinkId=253512)」を参照してください。  
  
-   64 ビット版 CLR をダウンロードする方法については、MSDN Web サイトの「[.NET Framework Developer Center Downloads](http://go.microsoft.com/fwlink/?LinkId=50953)」を参照してください。  
  
-   64 ビット アプリケーションを作成するための Visual Studio のサポート機能については、「[Visual Studio IDE の 64 ビット サポート](../Topic/Visual%20Studio%20IDE%2064-Bit%20Support.md)」を参照してください。  
  
## 64 ビット アプリケーションを作成するためのコンパイラのサポート  
 既定では、.NET Framework を使用して 32 ビット コンピューターまたは 64 ビット コンピューターでアプリケーションをビルドする場合、アプリケーションは 64 ビット コンピューターでネイティブ アプリケーションとして \(WOW64 の制御下ではなく\) 実行します。  次の表に、Visual Studio コンパイラを使用して、ネイティブなアプリケーションとして実行する 64 ビット アプリケーション、WOW64 の下で実行する 64 ビット アプリケーション、またはその両方が可能な 64 ビット アプリケーションを作成するための方法を説明するドキュメントを示します。  
  
|コンパイラ|コンパイラ オプション|  
|-----------|-----------------|  
|Visual Basic|[\/platform](../Topic/-platform%20\(Visual%20Basic\).md)|  
|Visual C\#|[\/platform \(Specify Output Platform\)](../Topic/-platform%20\(C%23%20Compiler%20Options\).md)|  
|Visual C\+\+|**\/clr:safe** を使用すると、プラットフォームに依存しない、Microsoft Intermediate Language \(MSIL\) アプリケーションを作成できます。  詳しくは、「[\/clr \(共通言語ランタイムのコンパイル\)](../Topic/-clr%20\(Common%20Language%20Runtime%20Compilation\).md)」を参照してください。<br /><br /> Visual C\+\+ には、それぞれの 64 ビット オペレーティング システムを対象とする個別のコンパイラが含まれます。  Visual C\+\+ を使用して 64 ビット Windows オペレーティング システム上で実行するネイティブ アプリケーションを作成する方法の詳細については、「[64\-bit Programming](http://msdn.microsoft.com/library/h2k70f3s\(v=vs.80\))」を参照してください。|  
  
## .exe ファイルまたは .dll ファイルのステータスの特定  
 .exe ファイルまたは .dll ファイルが、特定のプラットフォーム上または WOW64 の下でのみ動作するように意図されているかどうかを確認するには、[CorFlags.exe \(CorFlags 変換ツール\)](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md) を使用します \(オプションは指定しません\)。  また、CorFlags.exe を使用して、.exe ファイルまたは .dll ファイルのプラットフォームのステータスを変更することもできます。  Visual Studio アセンブリの CLR ヘッダーのメジャー ランタイム バージョン番号が 2、マイナー ランタイム バージョン番号が 5 に設定されています。  マイナー ランタイム バージョンが 0 に設定されたアプリケーションは、レガシ アプリケーションとして扱われ、常に WOW64 の下で実行されます。  
  
 プログラムによって .exe または .dll を照会し、それが特定のプラットフォーム上または WOW64 の下でのみ動作するように意図されているかどうかを確認するには、<xref:System.Reflection.Module.GetPEKind%2A?displayProperty=fullName> メソッドを使用します。