---
title: "方法: COM ラッパーを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM, ラッパーの作成"
  - "COM, ラッパー Visual Studio"
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法: COM ラッパーを作成する
コンポーネント オブジェクト モデル \(COM: Component Object Model\) ラッパーを作成するには、[!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] の機能または .NET Framework のツールである Tlbimp.exe と Regasm.exe を使用します。  どちらの方法でも 2 種類の COM ラッパーが生成されます。  
  
-   タイプ ライブラリからの[ランタイム呼び出し可能ラッパー](../../../docs/framework/interop/runtime-callable-wrapper.md)。COM オブジェクトをマネージ コードで実行します。  
  
-   必要なレジストリ設定を含む [COM 呼び出し可能ラッパー](../../../docs/framework/interop/com-callable-wrapper.md)。マネージ オブジェクトをネイティブ アプリケーションで実行します。  
  
 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] では、COM ラッパーを参照としてプロジェクトに追加できます。  
  
## マネージ アプリケーションでの COM オブジェクトのラップ  
  
#### Visual Studio を使用してランタイム呼び出し可能ラッパーを作成するには  
  
1.  マネージ アプリケーションのプロジェクトを開きます。  
  
2.  **\[プロジェクト\]** メニューの **\[すべてのファイルを表示\]** をクリックします。  
  
3.  **\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。  
  
4.  \[参照の追加\] ダイアログ ボックスで、**\[COM\]** タブをクリックし、使用するコンポーネントを選択して **\[OK\]** をクリックします。  
  
     **ソリューション エクスプローラー**で、プロジェクトの \[参照設定\] フォルダーに COM コンポーネントが追加されていることを確認します。  
  
 これで、COM オブジェクトにアクセスするためのコードを作成できます。  まずオブジェクトを宣言します。これには、[!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] の `Imports` ステートメント、[!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)] の `Using` ステートメントなどを使用します。  
  
> [!NOTE]
>  Microsoft Office コンポーネントをプログラミングする場合は、最初に Microsoft ダウンロード センターから [Microsoft Office プライマリ相互運用機能アセンブリ](http://go.microsoft.com/fwlink/?LinkId=50479) \(PIA: Primary Interop Assembly\) をインストールします。  手順 4. で、目的の Office 製品向けに用意されているオブジェクト ライブラリの最新バージョンを選択します \(**Microsoft Word 11.0 Object Library** など\)。  [](http://msdn.microsoft.com/ja-jp/c9d2a8b9-69df-4c0b-90ca-4d85bae063c4)  
  
#### .NET Framework のツールを使用してランタイム呼び出し可能ラッパーを作成するには  
  
-   [Tlbimp.exe \(タイプ ライブラリ インポーター\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) ツールを実行します。  
  
 このツールは、元のタイプ ライブラリで定義された型のランタイム メタデータを含むアセンブリを作成します。  
  
## ネイティブ アプリケーションでのマネージ オブジェクトのラップ  
  
#### Visual Studio を使用して COM 呼び出し可能ラッパーを作成するには  
  
1.  ネイティブ コードで実行するマネージ クラス用にクラス ライブラリ プロジェクトを作成します。  このクラスには既定のコンストラクターが必要です。  
  
     AssemblyInfo ファイル内で、4 つの部分で構成される完全なバージョン番号がアセンブリに指定されていることを確認します。  この番号は、Windows レジストリでバージョンを管理するために必要となります。  バージョン番号の詳細については、「[アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)」を参照してください。  
  
2.  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
3.  **\[コンパイル\]** タブをクリックします。  
  
4.  **\[COM の相互運用機能に登録\]** チェック ボックスをオンにします。  
  
 プロジェクトをビルドすると、COM 相互運用機能に対してアセンブリが自動的に登録されます。  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] でネイティブ アプリケーションをビルドする場合は、**\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックすることでアセンブリを使用できます。  
  
#### .NET Framework のツールを使用して COM 呼び出し可能ラッパーを作成するには  
  
-   [Regasm.exe \(アセンブリ登録ツール\)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) ツールを実行します。  
  
 このツールは、アセンブリ メタデータを読み取って、必要なエントリをレジストリに追加します。  この結果、COM クライアントが .NET Framework クラスを透過的に作成できるようになります。  アセンブリは、ネイティブ COM クラスと同じように使用できます。  
  
 任意のディレクトリにあるアセンブリで Regasm.exe を実行し、さらに[Gacutil.exe \(グローバル アセンブリ キャッシュ ツール\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を実行してそのアセンブリをグローバル アセンブリ キャッシュに移動できます。  アセンブリを移動しても、場所のレジストリ エントリは無効になりません。これは、アセンブリが他の場所で見つからない場合に常にグローバル アセンブリ キャッシュが調べられるからです。  
  
## 参照  
 [ランタイム呼び出し可能ラッパー](../../../docs/framework/interop/runtime-callable-wrapper.md)   
 [COM 呼び出し可能ラッパー](../../../docs/framework/interop/com-callable-wrapper.md)