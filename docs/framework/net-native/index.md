---
title: ".NET ネイティブによるアプリのコンパイル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET とネイティブ コード"
  - ".NET Native"
  - "C# とネイティブ コンパイル"
  - ".NET ネイティブによるコンパイル"
  - "ネイティブ コンパイル"
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: 27
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 27
---
# .NET ネイティブによるアプリのコンパイル
[!INCLUDE[net_native](../../../includes/net-native-md.md)] は、Windows アプリをビルドして配置するためのプリコンパイル テクノロジで、[!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)] に含まれています。 マネージ コード \(C\# または Visual Basic\) で記述された、.NET Framework および Windows 10 を対象とするアプリのリリース バージョンを自動的にネイティブ コードにコンパイルします。  
  
 通常、.NET Framework を対象とするアプリは中間言語 \(IL\) にコンパイルされます。 実行時に、Just\-In\-Time \(JIT\) コンパイラによって IL がネイティブ コードに変換されます。 これに対し、[!INCLUDE[net_native](../../../includes/net-native-md.md)]は、Windows アプリを直接ネイティブ コードにコンパイルします。 開発者にとって、これは次のことを意味します。  
  
-   アプリは、ネイティブ コードの優れたパフォーマンスを提供します。  
  
-   引き続き C\# または Visual Basic でプログラムを作成できます。  
  
-   クラス ライブラリ、自動メモリ管理とガベージ コレクション、例外処理など、.NET Framework で提供されるリソースを引き続き利用できます。  
  
 アプリのユーザーにとっては、[!INCLUDE[net_native](../../../includes/net-native-md.md)]には次のような利点があります。  
  
-   実行時間の短縮  
  
-   常に迅速に起動  
  
-   配置と更新コストの削減  
  
-   アプリのメモリ使用量の最適化  
  
 ただし、[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、ネイティブ コードへのコンパイル以上の操作が行われます。 .NET Framework アプリのビルド方法と実行方法が変更されます。 特に次の点に注意してください。  
  
-   プリコンパイル時に、.NET Framework の必要な部分がアプリに静的にリンクされます。 これにより、アプリは .NET Framework のアプリ ローカルのライブラリを使用して実行でき、コンパイラはグローバル分析を実行してパフォーマンスを向上させることができます。 その結果、.NET Framework の更新後であっても、アプリは常に高速に起動します。  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] ランタイムは静的プリコンパイル用に最適化されているため、優れたパフォーマンスを提供できます。 同時に、開発者に役立つ主要なリフレクション機能もあります。  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)]は、静的プリコンパイル シナリオ用に最適化されている、C\+\+ コンパイラと同じバックエンドを使用します。  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]は、この表に示すように、内部で C\+\+ と同じか類似のツールを使用しているため、マネージド コードの開発者に C\+\+ のパフォーマンス上の利点を提供できます。  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|C\+\+|  
|-|----------------------------------------------------------------|-----------|  
|ライブラリ|.NET Framework \+ Windows ランタイム|Win32 \+ Windows ランタイム|  
|コンパイラ|UTC 最適化コンパイラ|UTC 最適化コンパイラ|  
|配置|実行可能バイナリ|実行可能バイナリ \(ASM\)|  
|ランタイム|MRT.dll \(最小 CLR ランタイム\)|CRT.dll \(C ランタイム\)|  
  
 Windows 10 用の Windows アプリの場合は、.NET ネイティブ コード コンパイル バイナリをアプリ パッケージ \(.appx ファイル\) に入れて Windows ストアにアップロードします。  
  
## このセクションの内容  
 .NET ネイティブ コード コンパイルを使用したアプリ開発の詳細については、次のトピックを参照してください。  
  
-   [.NET ネイティブ コード コンパイルの概要: 開発者向けチュートリアル](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   [.NET ネイティブとコンパイル:](../../../docs/framework/net-native/net-native-and-compilation.md) .NET ネイティブがプロジェクトをネイティブ コードにコンパイルする方法を取り上げます。  
  
-   [リフレクションおよび .NET ネイティブ](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [リフレクションに依存する API](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [リフレクション API リファレンス](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [ランタイム ディレクティブ \(rd.xml\) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [シリアル化とメタデータ](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [Windows ストア アプリの .NET ネイティブへの移行](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [.NET ネイティブの一般的なトラブルシューティング](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## 参照  
 [.NET ネイティブに関する FAQ](http://msdn.microsoft.com/vstudio/dn642499.aspx)