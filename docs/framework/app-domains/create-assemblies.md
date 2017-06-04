---
title: "アセンブリの作成 | Microsoft Docs"
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
  - "アセンブリ [.NET Framework], 作成"
  - "アセンブリ [.NET Framework], マルチファイル"
  - "マルチファイル アセンブリ"
  - "シングルファイル アセンブリ"
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# アセンブリの作成
[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] などの IDE、または [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] に用意されているコンパイラとツールを使用して、シングルファイル アセンブリまたはマルチファイル アセンブリを作成できます。  最も単純なアセンブリであるシングルファイル アセンブリは、簡易名を持ち、1 つのアプリケーション ドメインに読み込まれます。  このアセンブリは、アプリケーション ディレクトリの外部にあるほかのアセンブリからは参照できず、バージョン チェックの対象にもなりません。  このアセンブリで構成されるアプリケーションをアンインストールするには、アセンブリが格納されているディレクトリを削除するだけですみます。  多くの開発者にとって、これらの機能を持つアセンブリは、アプリケーションの配置に必要なすべての機能を持っています。  
  
 複数のコード モジュールとリソース ファイルからマルチファイル アセンブリを作成できます。  複数のアプリケーションで共有するアセンブリを作成することもできます。  共有されるアセンブリは、厳密な名前を持つ必要があり、グローバル アセンブリ キャッシュ内に配置できます。  
  
 コード モジュールとリソースをグループ化したアセンブリを作成するときには、次の要素に基づいたいくつかのオプションを指定できます。  
  
-   バージョン管理  
  
     同じバージョン情報を持つモジュールをグループ化します。  
  
-   配置  
  
     使用する配置モデルをサポートするコード モジュールおよびリソースをグループ化します。  
  
-   再利用  
  
     用途別にまとめて論理的に使用できる場合、モジュールをグループ化します。  たとえば、プログラム保守のための、あまり使用しない型とクラスで構成されるアセンブリは、同じアセンブリに配置できます。  さらに、複数のアプリケーションで共有する型は、アセンブリ内にグループ化して厳密な名前で署名する必要があります。  
  
-   Security  
  
     同じセキュリティ アクセス許可を必要とする複数の型を含むモジュールをグループ化します。  
  
-   スコープの指定  
  
     参照可能範囲が同じアセンブリ内に制限されている型を含むモジュールをグループ化します。  
  
 共通言語ランタイムアセンブリをアンマネージ COM アプリケーションで使用できるようにする場合は、特別な考慮が必要です。  アンマネージ コードの使用の詳細については、「[COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)」を参照してください。  
  
## 参照  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)   
 [方法: シングルファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)   
 [方法 : マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [マルチファイル アセンブリ](../../../docs/framework/app-domains/multifile-assemblies.md)