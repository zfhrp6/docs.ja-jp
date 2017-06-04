---
title: "動的メソッドおよびアセンブリの出力 | Microsoft Docs"
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
  - "アセンブリ [.NET Framework], 出力 (動的アセンブリを)"
  - "動的アセンブリ"
  - "メタデータ, 出力 (インターフェイスを)"
  - "リフレクション出力"
  - "リフレクション出力, 概要"
ms.assetid: 8e8e2631-62fd-40e7-a8ee-0039b06749bc
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# 動的メソッドおよびアセンブリの出力
ここでは、<xref:System.Reflection.Emit> 名前空間のマネージ型のセットについて説明します。これらのマネージ型を使用すると、コンパイラやツールでメタデータおよび Microsoft Intermediate Language \(MSIL\) を実行時に出力できます。また、ポータブル実行可能 \(PE\) ファイルをディスク上に生成することもできます。  この名前空間を使用する主な機能は、スクリプト エンジンとコンパイラです。  ここでは、リフレクション出力と呼ばれる <xref:System.Reflection.Emit> 名前空間の機能について説明します。  
  
 リフレクション出力は、以下の機能を提供します。  
  
-   実行時に <xref:System.Reflection.Emit.DynamicMethod> クラスを使用して軽量のグローバル メソッドを定義し、デリゲートを使用してそのメソッドを実行します。  
  
-   実行時にアセンブリを定義し、次に、それらを実行するか、ディスクに保存します。  
  
-   実行時にアセンブリを定義し、それらを実行した後、それらをアンロードし、ガベージ コレクションがリソースを再利用できるようにします。  
  
-   実行時に新しいアセンブリのモジュールを定義し、次に、モジュールを実行するか、ディスクに保存します。  
  
-   実行時にモジュール内の型を定義し、その型のインスタンスを作成してメソッドを呼び出します。  
  
-   デバッガーまたはコード プロファイラなどのツールで使用できる、定義されたモジュールのシンボリック情報を定義します。  
  
 <xref:System.Reflection.Emit> 名前空間のマネージ型に加えて、アンマネージ メタデータ インターフェイスもあります。これについては、[メタデータ インターフェイス](../../../ocs/framework/unmanaged-api/metadata/metadata-interfaces.md)に関するリファレンス ドキュメントを参照してください。  マネージ リフレクション出力は、アンマネージ メタデータ インターフェイスよりも強力なセマンティック エラー チェック機能、より高水準なメタデータの抽象化クラスを提供します。  
  
 メタデータと MSIL を使用する際に役立つリソースとしては、他に、共通言語基盤 \(CLI: Common Language Infrastructure\) のドキュメント、特に「Partition II: Metadata Definition and Semantics」と「Partition III: CIL Instruction Set」などもあります。  ドキュメントは、[MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) および [Ecma Web サイト](http://go.microsoft.com/fwlink/?LinkId=116487) からオンラインで入手できます。  
  
## このセクションの内容  
 [リフレクション出力のセキュリティ関連事項](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 リフレクション出力を使用した動的アセンブリの作成時のセキュリティ関連事項について説明します。  
  
## 関連項目  
 <xref:System.Reflection.Emit.OpCodes>  
 メソッド本体の構築に使用できる MSIL 命令コードのカタログを作成します。  
  
 <xref:System.Reflection.Emit>  
 動的メソッド、アセンブリ、および型の出力に使用するマネージ クラスが含まれます。  
  
 <xref:System.Type>  
 <xref:System.Type> クラスについて説明します。このクラスは、マネージ リフレクションとリフレクション出力の型を表し、これらのテクノロジを使用するうえで重要なクラスです。  
  
 <xref:System.Reflection>  
 メタデータとマネージ コードの探索に使用するマネージ クラスが含まれます。  
  
## 関連項目  
 [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)  
 メタデータとマネージ コードの探索方法について説明します。  
  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 .NET Framework のアセンブリの概要を説明します。