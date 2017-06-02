---
title: ".NET Framework による複数のプラットフォームの開発 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# .NET Framework による複数のプラットフォームの開発
.NET Framework と Visual Studio を使用して、Microsoft プラットフォームと Microsoft 以外のプラットフォームの両方を対象としたアプリを開発できます。  
  
## クロスプラットフォーム開発のオプション  
 複数プラットフォームを対象として開発する場合は、ソース コードやバイナリを共有し、.NET Framework コードと Windows ランタイム API の間で呼び出しを実行できます。  
  
|目的|用途|  
|--------|--------|  
|Windows Phone 8.1 アプリと Windows 8.1 アプリの間でソース コードを共有する|**共有プロジェクト** \(Visual Studio 2013 更新プログラム 2 のユニバーサル アプリ テンプレート\).<br /><br /> -   Visual Basic は現在サポートされていません。<br />-   \#`if` ステートメントを使用してプラットフォーム固有のコードを分離できます。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [Visual Studio を使用した Windows と Windows Phone を対象とするアプリの構築](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx) \(MSDN 文書\)<br />-   [Using Visual Studio to build Universal XAML Apps \(Visual Studio を使用したユニバーサル XAML アプリの開発\)](http://blogs.msdn.com/b/visualstudio/archive/2014/04/14/using-visual-studio-to-build-universal-xaml-apps.aspx) \(ブログの投稿\)<br />-   [Using Visual Studio to Build XAML Converged Apps \(Visual Studio を使用した XAML コンバージド アプリの開発\)](http://channel9.msdn.com/Events/Build/2014/3-591) \(ビデオ\)|  
|異なるプラットフォームを対象とするアプリ間でバイナリを共有する|プラットフォームに依存しないコードの**ポータブル クラス ライブラリ プロジェクト**。<br /><br /> -   この方法は通常、ビジネス ロジックを実装するコードに使用されます。<br />-   Visual Basic または Visual C\# を使用できます。<br />-   API のサポートはプラットフォームによって異なります。<br />-   Windows 8.1 および Windows Phone 8.1 を対象としたポータブル クラス ライブラリのプロジェクトでは、Windows ランタイム API と XAML がサポートされます。  これらの機能は、古いバージョンのポータブル クラス ライブラリでは使用できません。<br />-   必要に応じて、インターフェイスまたは抽象クラスを使用してプラットフォーム固有のコードを抽象化できます。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [汎用性のあるクラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) \(MSDN 記事\)<br />-   [How to Make Portable Class Libraries Work for You \(ポータブル クラス ライブラリを活用する方法\)](http://blogs.msdn.com/b/dsplaisted/archive/2012/08/27/how-to-make-portable-class-libraries-work-for-you.aspx) \(ブログ記事\)<br />-   [MVVM を利用した汎用性のあるクラス ライブラリの使用](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md) \(MSDN 記事\)<br />-   [複数のプラットフォームを対象とするライブラリのアプリケーション リソース](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md) \(MSDN 記事\)<br />-   [.NET 移植性アナライザー](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b) \(Visual Studio の拡張機能\)|  
|Windows 8.1 および Windows Phone 8.1 以外のプラットフォームを対象としたアプリの間でソース コードを共有する|**\[リンクとして追加\]** 機能。<br /><br /> -   この方法は、両方のアプリに共通しているが、何らかの理由で移植できないアプリ ロジックに適しています。  この機能は Visual Basic または Visual C\# のコードに使用できます。<br />     たとえば Windows Phone 8 と Windows 8 は Windows ランタイム API を共有しますが、ポータブル クラス ライブラリはこれらのプラットフォームでは Windows ランタイムをサポートしていません。  Windows Phone 8 アプリと、Windows 8 を対象とした Windows ストア アプリの間で共通する Windows ランタイム コードを共有するには、`Add as link` を使用できます。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [\[リンクとして追加\] を使用してコードを共有する](http://msdn.microsoft.com/library/windowsphone/develop/jj714082\(v=vs.105\).aspx) \(MSDN article\)<br />-   [方法 : プロジェクトに既存の項目を追加する](http://msdn.microsoft.com/library/vstudio/9f4t9t92\(v=vs.100\).aspx) \(MSDN 文書\)|  
|.NET Framework を使用して Windows ストア アプリを作成するか、または .NET Framework コードから Windows ランタイム API を呼び出します。|.NET Framework C\# または Visual Basic コードの **Windows ランタイム API**。.NET Framework を使用して Windows ストア アプリを作成します。  2 つのプラットフォーム間の API の違いについて注意してください。  ただし、これらの違いに対処するためのクラスがあります。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md) \(MSDN 記事\)<br />-   [Windows ランタイムへの URI の引き渡し](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md) \(MSDN 記事\)<br />-   <xref:System.IO.WindowsRuntimeStreamExtensions> \(MSDN API リファレンス ページ\)<br />-   <xref:System.WindowsRuntimeSystemExtensions> \(MSDN API リファレンス ページ\)|  
|Microsoft 以外のプラットフォームに対応した .NET Framework アプリの開発|.NET Framework, の **ポータブル クラス ライブラリの参照アセンブリ**と、Visual Studio 拡張機能またはサードパーティ ツール \(Xamarin など\)。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [Portable Class Library now available on all platforms \(ポータブル クラス ライブラリ、全プラットフォームで使用可能に\)](http://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx) \(ブログの投稿\)<br />-   [Xamarin](http://xamarin.com/visual-studio) \(Xamarin Web サイト\)|  
|JavaScript および HTML を使用したクロスプラットフォーム開発|Visual Studio 2013 更新プログラム 2 の**ユニバーサル アプリ テンプレート**。このテンプレートを使用して、Windows 8.1 と Windows Phone 8.1 の Windows ランタイム API に対する開発を行います。  現在、クロスプラットフォーム アプリを開発するときに .NET Framework API で JavaScript と HTML を使用することはできません。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [JavaScript プロジェクト テンプレート](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx)<br />-   [JavaScript を使った Windows ランタイム アプリを Windows Phone に移植する方法](http://msdn.microsoft.com/library/windows/apps/dn636144.aspx)|