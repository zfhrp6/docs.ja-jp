---
title: "方法 : インストールされている .NET Framework バージョンを確認する | Microsoft Docs"
ms.custom: ""
ms.date: "04/07/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework, 確認 (バージョンを)"
  - "バージョン, 確認 (.NET Framework の)"
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
caps.latest.revision: 62
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 53
---
# 方法 : インストールされている .NET Framework バージョンを確認する
ユーザーはコンピューターに複数のバージョンの .NET Framework をインストールして実行できます。 アプリを開発または配置する場合、どのバージョンの .NET Framework がユーザーのコンピューターにインストールされているかを確認しなければならない場合があります。 .NET Framework は、個別にバージョン管理される 2 つの主要コンポーネントで構成されています。  
  
-   アプリに機能を提供する型やリソースのコレクションである一連のアセンブリ。 .NET Framework とアセンブリは同じバージョン番号を共有します。  
  
-   アプリのコードを管理および実行する共通言語ランタイム \(CLR\)。 CLR は独自のバージョン番号で識別されます \(「[バージョンおよび依存関係](../../../docs/framework/migration-guide/versions-and-dependencies.md)」を参照してください\)。  
  
 コンピューターにインストールされている .NET Framework バージョンの正確な一覧を取得するには、レジストリを表示するか、コードでレジストリを照会することができます。  
  
 [レジストリの表示 \(バージョン 1 ～ 4\)](#net_a)  
[レジストリの表示 \(バージョン 4.5 以降\)](#net_b)  
[コードによるレジストリの照会 \(バージョン 1 ～ 4\)](#net_c)  
[コードによるレジストリの照会 \(バージョン 4.5 以降\)](#net_d)  
  
 CLR のバージョンを検索するには、ツールまたはコードを使用できます。  
  
 [Clrver ツールの使用](#clr_a)  
[コードによる System.Environment クラスの照会](#clr_b)  
  
 .NET Framework の各バージョン用にインストールされている更新プログラムの検出については、「[方法 : インストールされている .NET Framework の更新プログラムを確認する](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)」を参照してください。 .NET Framework をインストールする方法については、[インストール ガイド](../../../docs/framework/install/guide-for-developers.md)を参照してください。  
  
<a name="net_a"></a>   
#### レジストリを表示して .NET Framework のバージョンを検索するには \(.NET Framework 1 ～ 4\)  
  
1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
2.  **\[開く\]** ボックスに「**regedit.exe**」と入力します。  
  
     regedit.exe を実行するには、管理特権が必要です。  
  
3.  レジストリ エディターで、次のサブキーを開きます。  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     インストールされているバージョンは NDP のサブキーの下に一覧表示されています。 バージョン番号は、**Version** エントリに格納されています。[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、**Version** エントリは、Client サブキーまたは Full サブキー \(NDP の下\)、または両方のサブキーの下にあります。  
  
    > [!NOTE]
    >  レジストリの ".NET Framework セットアップ" フォルダーの先頭はピリオドではありません。  
  
<a name="net_b"></a>   
#### レジストリを表示して .NET Framework のバージョンを検索するには \(.NET Framework 4.5 以降\)  
  
1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックします。  
  
2.  **\[開く\]** ボックスに「**regedit.exe**」と入力します。  
  
     regedit.exe を実行するには、管理特権が必要です。  
  
3.  レジストリ エディターで、次のサブキーを開きます。  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`  
  
     `Full` サブキーへのパスに `.NET Framework` ではなく `Net Framework` サブキーが含まれていることに注意してください。  
  
    > [!NOTE]
    >  `Full` サブキーが存在しない場合は、.NET Framework 4.5 以降がインストールされていません。  
  
     `Release` という名前の DWORD 値を確認します。`Release` DWORD がある場合は、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降がコンピューターにインストールされていることを示します。  
  
     ![.NET Framework 4.5 のレジストリ エントリ。](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR\_InstallDir")  
  
     `Release` の値は、インストールされている .NET Framework のバージョンを示します。  
  
    |Release DWORD の値|バージョン|  
    |----------------------|-----------|  
    |378389|.NET Framework 4.5|  
    |378675|Windows 8.1 または Windows Server 2012 R2 でインストールされた .NET Framework 4.5.1|  
    |378758|Windows 8、Windows 7 SP1、または Windows Vista SP2 上でインストールされた .NET Framework 4.5.1|  
    |379893|.NET Framework 4.5.2|  
    |Windows 10 システム上: 393295<br /><br /> その他すべての OS バージョン上: 393297|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|  
    |Windows 10 の 11 月更新版のシステムの場合: 394254<br /><br /> 他のすべての OS バージョンの場合: 394271|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|  
  
<a name="net_c"></a>   
#### コードでレジストリを照会して .NET Framework のバージョンを検索するには \(.NET Framework 1 ～ 4\)  
  
-   <xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> クラスを使用して、Windows レジストリの HKEY\_LOCAL\_MACHINE の下にある Software\\Microsoft\\NET Framework Setup\\NDP\\ サブキーにアクセスします。  
  
     このクエリの例を次のコードに示します。  
  
    > [!NOTE]
    >  このコードは [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降を検出する方法を示すコードではありません。 前のセクションで説明したように、これらのバージョンを検出するには、`Release` DWORD を確認してください。  
  
     [!code-csharp[ListVersions#0](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#0)]
     [!code-vb[ListVersions#0](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#0)]  
    [!code-csharp[ListVersions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#1)]
    [!code-vb[ListVersions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#1)]  
  
     この例では次のような出力が生成されます。  
  
    ```  
  
    v2.0.50727  2.0.50727.4016  SP2 v3.0  3.0.30729.4037  SP2 v3.5  3.5.30729.01  SP1 v4 Client  4.0.30319 Full  4.0.30319  
    ```  
  
<a name="net_d"></a>   
#### コードでレジストリを照会して .NET Framework のバージョンを検索するには \(.NET Framework 4.5 以降\)  
  
1.  `Release` DWORD がある場合は、.NET Framework 4.5 以降がコンピューターにインストールされています。 キーワードの値はインストールされているバージョンを示します。 このキーワードを確認するには、<xref:Microsoft.Win32.RegistryKey?displayProperty=fullName> クラスの <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> メソッドと <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> メソッドを使って、Windows レジストリの HKEY\_LOCAL\_MACHINE の下にある Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full サブキーにアクセスします。  
  
2.  `Release` キーワードの値を確認して、インストールされているバージョンを決定します。 上位互換性を確認するには、テーブルに示されている値以上の値があるかを確認します。 .NET Framework のバージョンと関連付けられた `Release` キーワードを次に示します。  
  
    |バージョン|Release DWORD の値|  
    |-----------|----------------------|  
    |.NET Framework 4.5|378389|  
    |Windows 8.1 でインストールされた .NET Framework 4.5.1|378675|  
    |Windows 8、Windows 7 SP1、または Windows Vista SP2 上でインストールされた .NET Framework 4.5.1|378758|  
    |.NET Framework 4.5.2|379893|  
    |Windows 10 にインストールされた [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|393295|  
    |その他のすべての Windows OS バージョンにインストールされた [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|393297|  
    |Windows 10 にインストールされる [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|394254|  
    |その他のすべての Windows OS バージョンにインストールされた [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|394271|  
  
     各バージョンの release キーワードの値以上の値を確認する例を次に示します。  
  
     [!code-csharp[ListVersions#0](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#0)]
     [!code-vb[ListVersions#0](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#0)]  
    [!code-csharp[ListVersions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#3)]
    [!code-vb[ListVersions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#3)]  
    [!code-csharp[ListVersions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#4)]
    [!code-vb[ListVersions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#4)]  
  
     この例では次のような出力が生成されます。  
  
    ```  
    Version: 4.5.1 or later  
    ```  
  
<a name="clr_a"></a>   
#### Clrver ツールを使用して現在のランタイムのバージョンを確認する方法  
  
-   CLR バージョン ツール \(Clrver.exe\) を使用して、コンピューターにインストールされている共通言語ランタイムのバージョンを確認します。  
  
     Visual Studio コマンド プロンプトで、「`clrver`」と入力します。 次のような出力が表示されます。  
  
    ```  
    Versions installed on the machine: v2.0.50727 v4.0.30319  
    ```  
  
     このツールの使用方法の詳細については、「[Clrver.exe \(CLR バージョン ツール\)](../../../docs/framework/tools/clrver-exe-clr-version-tool.md)」を参照してください。  
  
<a name="clr_b"></a>   
#### コードで Environment クラスを照会して現在のランタイム バージョンを確認するには  
  
-   <xref:System.Environment.Version%2A?displayProperty=fullName> プロパティを照会して <xref:System.Version> オブジェクトを取得し、現在コードを実行しているランタイムのバージョンを識別します。 メジャー リリースの識別子 \(バージョン 4.0 の "4" など\) を取得するには <xref:System.Version.Major%2A?displayProperty=fullName> プロパティを、マイナー リリースの識別子 \(バージョン 4.0 の "0" など\) を取得するには <xref:System.Version.Minor%2A?displayProperty=fullName> プロパティを、バージョン文字列全体 \(次のコードに示すような "4.0.30319.18010" など\) を取得するには <xref:System.Object.ToString%2A?displayProperty=fullName> メソッドを使用できます。 このプロパティは、現在コードを実行しているランタイムのバージョンを表す単一の値を返しますが、アセンブリのバージョンやコンピューターにインストールされている可能性があるランタイムの他のバージョンは返しません。  
  
     .NET Framework バージョン 4、4.5、4.5.1、および 4.5.2 の場合は、<xref:System.Environment.Version%2A?displayProperty=fullName> プロパティから返される <xref:System.Version> オブジェクトの文字列表現が `4.0.30319.xxxxx` という形式になっています。[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] の場合は、そのフォームは `4.0.30319.42000` となります。  
  
     次に、<xref:System.Environment.Version%2A?displayProperty=fullName> プロパティを照会してランタイム バージョン情報を取得する例を示します。  
  
     [!code-csharp[ListVersions#0](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#0)]
     [!code-vb[ListVersions#0](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#0)]  
    [!code-csharp[ListVersions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/listversions/cs/program.cs#2)]
    [!code-vb[ListVersions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listversions/vb/program.vb#2)]  
  
     この例では次のような出力が生成されます。  
  
    ```  
    Version: 4.0.30319.18010  
    ```  
  
## 参照  
 [方法 : インストールされている .NET Framework の更新プログラムを確認する](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)   
 [インストール ガイド](../../../docs/framework/install/guide-for-developers.md)   
 [バージョンおよび依存関係](../../../docs/framework/migration-guide/versions-and-dependencies.md)