---
title: "EDM ジェネレーター (EdmGen.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# EDM ジェネレーター (EdmGen.exe)
EdmGen.exe は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] モデルとマッピング ファイルを操作するためのコマンドライン ツールです。  EdmGen.exe ツールを使用すると、次の操作を行うことができます。  
  
-   データ ソース固有の .NET Framework データ プロバイダーを使用してデータ ソースに接続し、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で使用される概念モデル \(.csdl\)、ストレージ モデル \(.ssdl\)、およびマッピング \(.msl\) のファイルを生成する。  詳細については、「[方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)」を参照してください。  
  
-   既存のモデルを検証する。  詳細については、「[方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)」を参照してください。  
  
-   概念モデル \(.csdl\) ファイルから生成されたオブジェクト クラスを含む C\# コード ファイルまたは Visual Basic コード ファイルを生成する。  詳細については、「[方法: EdmGen.exe を使用してオブジェクトレイヤー コードを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)」を参照してください。  
  
-   事前に生成した既存のモデルのビューを含む C\# コード ファイルまたは Visual Basic コード ファイルを生成する。  詳細については、「[How to: Pre\-Generate Views to Improve Query Performance](http://msdn.microsoft.com/ja-jp/b18a9d16-e10b-4043-ba91-b632f85a2579)」を参照してください。  
  
 EdmGen.exe ツールは [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] ディレクトリにインストールされます。  多くの場合、C:\\windows\\Microsoft.NET\\Framework\\v4.0 にあります。  64 ビット システムの場合は、C:\\windows\\Microsoft.NET\\Framework64\\v4.0 にあります。  Visual Studio のコマンド プロンプトから EdmGen.exe ツールにアクセスすることもできます \(**\[スタート\]** ボタンをクリックし、**\[すべてのプログラム\]**、**\[Microsoft Visual Studio 2010\]**、**\[Visual Studio ツール\]** の順にポイントして、**\[Visual Studio 2010 コマンド プロンプト\]** をクリックします\)。  
  
## 構文  
  
```  
EdmGen /mode:choice [options]  
```  
  
## モード  
 EdmGen.exe ツールを使用する場合、次のいずれかのモードを指定する必要があります。  
  
|モード|説明|  
|---------|--------|  
|`/mode:ValidateArtifacts`|.csdl、.ssdl、および .msl ファイルを検証し、エラーまたは警告を表示します。<br /><br /> このオプションを使用するには、少なくとも `/inssdl` 引数または `/incsdl` 引数のどちらかが必要です。  `/inmsl` を指定する場合は、`/inssdl` 引数と `/incsdl` 引数も必要です。|  
|`/mode:FullGeneration`|`/connectionstring` オプションで指定されたデータベース接続情報を使用し、.csdl、.ssdl、.msl、オブジェクト レイヤー、およびビュー ファイルを生成します。<br /><br /> このオプションを使用するには、`/connectionstring` 引数に加え、`/project` 引数を指定するか、`/outssdl`、`/outcsdl`、`/outmsdl`、`/outobjectlayer`、`/outviews`、`/namespace`、`/entitycontainer` の各引数を指定する必要があります。|  
|`/mode:FromSSDLGeneration`|指定された .ssdl ファイルから、.csdl ファイル、.msl ファイル、ソース コード、およびビューを生成します。<br /><br /> このオプションを使用するには、`/inssdl` 引数に加え、`/project` 引数を指定するか、`/outcsdl`、`/outmsl`、`/outobjectlayer`、`/outviews`、、`/entitycontainer` の各引数を指定する必要があります。|  
|`/mode:EntityClassGeneration`|.csdl ファイルから生成されたクラスを含むソース コード ファイルを作成します。<br /><br /> このオプションを使用するには、`/incsdl` 引数に加え、`/project` 引数または `/outobjectlayer` 引数のどちらかを指定する必要があります。  `/language` 引数は省略可能です。|  
|`/mode:ViewGeneration`|.csdl、.ssdl、および .msl ファイルから生成されたビューを含むソース コード ファイルを作成します。<br /><br /> このオプションを使用するには、`/inssdl`、`/incsdl`、 の各引数に加え、`/project` 引数または `/outviews` 引数のどちらかを指定する必要があります。  `/language` 引数は省略可能です。|  
  
## オプション  
  
|オプション|説明|  
|-----------|--------|  
|`/p[roject]:`\<string\>|使用するプロジェクト名を指定します。  このプロジェクト名は、名前空間の設定の既定値、モデル ファイルとマッピング ファイルの名前、オブジェクト ソース ファイルの名前、およびビュー生成のソース ファイルの名前として使用されます。  エンティティのコンテナ名が \<project\>Context に設定されています。|  
|`/prov[ider]:`\<string\>|ストレージ モデル \(.ssdl\) ファイルの生成に使用する [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] データ プロバイダーの名前です。  既定のプロバイダーは [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server \(<xref:System.Data.SqlClient?displayProperty=fullName>\) です。|  
|`/c[onnectionstring]:`\<connection string\>|データ ソースへの接続に使用する文字列を指定します。|  
|`/incsdl:`\<file\>|.csdl ファイル、または .csdl ファイルがあるディレクトリを指定します。  この引数は複数回指定できるので、複数のディレクトリまたは .csdl ファイルを指定できます。  概念モデルが複数のファイルに分割されている場合にクラスの生成 \(`/mode:EntityClassGeneration`\) またはビューの生成 \(`/mode:ViewGeneration`\) を行うときは、複数のディレクトリを指定すると便利です。  また、複数のモデルを検証する \(`/mode:ValidateArtifacts`\) 場合にも役立ちます。|  
|`/refcsdl:`\<file\>|追加の .csdl ファイル、またはソース .csdl ファイルの参照の解決に使用するファイルを指定します   \(ソース .csdl ファイルは、`/incsdl` オプションで指定したファイルです\)。  `/refcsdl` ファイルには、ソース .csdl ファイルが依存する型が含まれています。  この引数は複数回指定できます。|  
|`/inmsl:`\<file\>|.msl ファイル、または .msl ファイルがあるディレクトリを指定します。  この引数は複数回指定できるので、複数のディレクトリまたは .msl ファイルを指定できます。  概念モデルが複数のファイルに分割されている場合にビューを生成 \(`/mode:ViewGeneration`\) するときは、複数のディレクトリを指定すると便利です。  また、複数のモデルを検証する \(`/mode:ValidateArtifacts`\) 場合にも役立ちます。|  
|`/inssdl:`\<file\>|.ssdl ファイル、または .ssdl ファイルがあるディレクトリを指定します。  この引数は複数回指定できるので、複数のディレクトリまたは .ssdl ファイルを指定できます。  これは、複数のモデルを検証する場合 `(/mode:ValidateArtifacts)` に役立ちます。|  
|`/outcsdl:`\<file\>|作成される .csdl ファイルの名前を指定します。|  
|`/outmsl:`\<file\>|作成される .msl ファイルの名前を指定します。|  
|`/outssdl:`\<file\>|作成される .ssdl ファイルの名前を指定します。|  
|`/outobjectlayer:`\<file\>|.csdl ファイルから生成されたオブジェクトを含むソース コード ファイルの名前を指定します。|  
|`/outviews:`\<file\>|生成されたビューを含むソース コード ファイルの名前を指定します。|  
|`/language:`\[VB&#124;CSharp\]|生成されるソース コード ファイルの言語を指定します。  既定の言語は C\# です。|  
|`/namespace:`\<string\>|使用するモデル名前空間を指定します。  名前空間は、`/mode:FullGeneration` または `/mode:FromSSDLGeneration` の実行時に .csdl ファイルに設定されます。  `/mode:EntityClassGeneration` の実行時には名前空間は使用されません。|  
|`/entitycontainer:`\<string\>|生成されたモデル ファイルとマッピング ファイルの `<EntityContainer>` 要素に適用する名前を指定します。|  
|`/pl[uralize]`|単数形と複数形の英語のルールを、概念モデルの `Entity`、`EntitySet`、および `NavigationProperty` の各名前に適用します。  このオプションでは、以下の処理が実行されます。<br /><br /> -   `EntityType` 名がすべて単数形になります。<br />-   `EntitySet` 名がすべて複数形になります。<br />-   各 `NavigationProperty` が返すエンティティが最大で 1 つの場合、名前は単数形になります。<br />-   各 `NavigationProperty` が返すエンティティが複数の場合、名前は複数形になります。|  
|`/SupressForeignKeyProperties or /nofk`|外部キー列が概念モデルのエンティティ型のスカラー プロパティとして公開されないようにします。|  
|`/help` または`?`|このツールのコマンド構文とオプションを表示します。|  
|`/nologo`|著作権メッセージが表示されないようにします。|  
|`/targetversion:` \<string\>|生成されたコードのコンパイルに使用される .NET Framework のバージョンです。  サポートされているバージョンは 4 と 4.5 です。  既定値は 4 です。|  
  
## このセクションの内容  
 [方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)  
  
 [方法: EdmGen.exe を使用してオブジェクトレイヤー コードを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)  
  
 [方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)  
  
## 参照  
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/ja-jp/91076853-0881-421b-837a-f582f36be527)   
 [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)   
 [CSDL、SSDL、および MSL 仕様](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)