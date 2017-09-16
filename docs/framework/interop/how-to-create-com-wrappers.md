---
title: "方法: COM ラッパーを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e99b084ddb565a8ae00ee917eaf7fca2c659ab64
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-create-com-wrappers"></a>方法: COM ラッパーを作成する
[!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] の機能または .NET Framework のツールである Tlbimp.exe と Regasm.exe を使用して、COM (コンポーネント オブジェクト モデル) ラッパーを作成することができます。 どちらの方法でも以下の 2 種類の COM ラッパーが作成されます。  
  
-   タイプ ライブラリからの[ランタイム呼び出し可能ラッパー](../../../docs/framework/interop/runtime-callable-wrapper.md)。マネージ コードで COM オブジェクトを実行します。  
  
-   必要なレジストリ設定を含む [COM 呼び出し可能ラッパー](../../../docs/framework/interop/com-callable-wrapper.md)。ネイティブ アプリケーションでマネージ オブジェクトを実行します。  
  
 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] では、プロジェクトに参照として COM ラッパーを追加できます。  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a>マネージ アプリケーションでの COM オブジェクトのラップ  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Visual Studio を使用してランタイム呼び出し可能ラッパーを作成するには  
  
1.  マネージ アプリケーションのプロジェクトを開きます。  
  
2.  **[プロジェクト]** メニューの **[すべてのファイルを表示]** をクリックします。  
  
3.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。  
  
4.  [参照の追加] ダイアログ ボックスで、**[COM]** タブをクリックし、使用するコンポーネントを選択して **[OK]** をクリックします。  
  
     **ソリューション エクスプローラー**で、COM コンポーネントがプロジェクトの [参照設定] フォルダーに追加されていることを確認します。  
  
 これで、COM オブジェクトにアクセスするためのコードを作成できます。 まず、`Imports` ステートメント ([!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] の場合) または `Using` ステートメント ([!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)] の場合) などのオブジェクトを宣言します。  
  
> [!NOTE]
>  Microsoft Office コンポーネントをプログラミングする場合は、最初に Microsoft ダウンロード センターから [Microsoft Office プライマリ相互運用機能アセンブリ](http://go.microsoft.com/fwlink/?LinkId=50479) (PIA) をインストールします。 手順 4 で、必要な Office 製品で使用可能な最新バージョンのオブジェクト ライブラリ (**Microsoft Word 11.0 Object Library** など) を選択します。  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>.NET Framework ツールを使用してランタイム呼び出し可能ラッパーを作成するには  
  
-   [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) ツールを実行します。  
  
 このツールは、元のタイプ ライブラリで定義された型のランタイム メタデータを含むアセンブリを作成します。  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a>ネイティブ アプリケーションでのマネージ オブジェクトのラップ  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Visual Studio を使用して COM 呼び出し可能ラッパーを作成するには  
  
1.  ネイティブ コードで実行するマネージ クラス用のクラス ライブラリ プロジェクトを作成します。 このクラスには既定のコンストラクターが必要です。  
  
     AssemblyInfo ファイルで、アセンブリの 4 つの部分で構成される完全なバージョン番号があることを確認します。 この番号は、Windows レジストリでバージョンを管理するために必要となります。 バージョン番号の詳細については、「[アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)」を参照してください。  
  
2.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
3.  **[コンパイル]** タブをクリックします。  
  
4.  **[COM の相互運用機能に登録]** チェック ボックスをオンにします。  
  
 プロジェクトをビルドすると、アセンブリが COM 相互運用機能に対して自動的に登録されます。 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] でネイティブ アプリケーションをビルドする場合は、**[プロジェクト]** メニューの **[参照の追加]** をクリックすることで、アセンブリを使用できます。  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>.NET Framework ツールを使用して COM 呼び出し可能ラッパーを作成するには  
  
-   [Regasm.exe (アセンブリ登録ツール)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) を実行します。  
  
 このツールはアセンブリ メタデータを読み取り、必要なエントリをレジストリに追加します。 その結果、COM クライアントで .NET Framework クラスを透過的に作成できるようになります。 アセンブリは、ネイティブ COM クラスの場合と同じように使用することができます。  
  
 任意のディレクトリにあるアセンブリで Regasm.exe を実行してから、[Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を実行して、そのアセンブリをグローバル アセンブリ キャッシュに移動することができます。 アセンブリを移動しても場所のレジストリ エントリが無効になることはありません。これは、アセンブリが他の場所で見つからない場合に常にグローバル アセンブリ キャッシュが調べられるからです。  
  
## <a name="see-also"></a>関連項目  
 [ランタイム呼び出し可能ラッパー](../../../docs/framework/interop/runtime-callable-wrapper.md)   
 [COM 呼び出し可能ラッパー](../../../docs/framework/interop/com-callable-wrapper.md)

