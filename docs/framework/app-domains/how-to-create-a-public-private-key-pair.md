---
title: "方法 : 公開キーと秘密キーのキー ペアを作成する | Microsoft Docs"
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
  - "キー ペア (厳密な名前を持つアセンブリの)"
  - "署名 (アセンブリに)"
  - "アセンブリ [.NET Framework]、署名"
  - "暗号化キー ペア"
  - "snk ファイル (キー ペア ファイル)"
  - "公開キーと秘密キーのペア"
  - ".snk ファイル"
  - "厳密な名前を持つアセンブリ、キー ペア"
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 公開キーと秘密キーのキー ペアを作成する
厳密な名前でアセンブリに署名するには、公開キーと秘密キーのキー ペアが必要です。  公開キーと秘密キーの暗号キー ペアは、コンパイル中に厳密な名前付きアセンブリを作成するために使用されます。  キー ペアは、[厳密名ツール \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用して生成できます。  通常、キー ペア ファイルには、.snk 拡張子が付きます。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] では、C\# および Visual Basic プロジェクトのプロパティ ページに **\[署名\]** タブがあります。このタブでは、既存のキー ファイルを選択したり、Sn.exe を使用せずに新しいキー ファイルを生成したりできます。  Visual C\+\+ では、**\[プロパティ ページ\]** ウィンドウの **\[構成プロパティ\]** セクションの **\[リンカー\]** セクションにある **\[詳細\]** プロパティ ページで、既存のキー ファイルの場所を指定できます。  <xref:System.Reflection.AssemblyKeyFileAttribute> 属性を使用したキー ファイル ペアの指定は、[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 以降では行われなくなりました。  
  
### ユーザー コントロールを作成するには、次のようにします。  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     **sn –k** の \<*ファイル名*\>  
  
     このコマンドで、*file name* はキー ペアを格納する出力ファイルの名前です。  
  
 キー ペア `sgKey.snk` を作成する例を次に示します。  
  
```  
sn -k sgKey.snk  
```  
  
 アセンブリに遅延署名してキー ペア全体を制御する場合 \(通常、テスト シナリオでだけ実行できます\) は、次のコマンドを使用して、キー ペアを生成し、そのキー ペアから公開キーを別のファイルに抽出できます。  最初に、キー ペアを作成します。  
  
```  
sn -k keypair.snk  
```  
  
-   次に、キー ペアから公開キーを抽出し、別のファイルにコピーします。  
  
```  
sn -p keypair.snk public.snk  
```  
  
-   キー ペアの作成後に、厳密な名前の署名ツールが検出できる場所にファイルを配置する必要があります。  
  
 厳密な名前でアセンブリに署名すると、[アセンブリ リンカー \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) は、現在のディレクトリと出力ディレクトリを基準にしてキー ファイルを検索します。  コマンド ライン コンパイラを使用する場合は、コード モジュールを格納する現在のディレクトリにキーをコピーするだけで十分です。  
  
 プロジェクト プロパティに **\[署名\]** タブがない以前のバージョンの [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用している場合は、キー ファイルの場所として、次のようにファイル属性を指定したプロジェクト ディレクトリを使用することをお勧めします。  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
## 参照  
 [厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)