---
title: "アセンブリの作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c131e82e2312e2c1b7fe1b6b2b6d0a6dfb626209
ms.contentlocale: ja-jp
ms.lasthandoff: 06/02/2017

---
# <a name="creating-assemblies"></a>アセンブリの作成
[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] などの IDE を使用して単一ファイルまたはマルチファイルのアセンブリを作成したり、[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] から提供されるコンパイラやツールを作成したりすることができます。 最も単純なアセンブリは、単純な名前を持ち、単一のアプリケーション ドメインに読み込まれる単一のファイルです。 このアセンブリはアプリケーション ディレクトリの外部にある他のアセンブリからは参照できず、バージョン チェックが行われません。 アセンブリで構成されるアプリケーションをアンインストールするには、アプリケーションが存在するディレクトリを削除します。 多くの開発者は、このような機能を含むアセンブリがあれば、アプリケーションを展開できます。  
  
 マルチファイル アセンブリは、複数のコード モジュールおよびリソース ファイルから作成できます。 複数のアプリケーションで共有できるアセンブリも作成できます。 共有アセンブリは厳密な名前を持つ必要があり、グローバル アセンブリ キャッシュに展開することができます。  
  
 コード モジュールとリソースをアセンブリにグループ化する場合、次のような要因に応じていくつかのオプションがあります。  
  
-   バージョン管理  
  
     同じバージョン情報が含まれている必要があるグループ モジュール。  
  
-   配置  
  
     展開のモデルをサポートするグループ コードのモジュールおよびリソース。  
  
-   再利用  
  
     いくつかの目的のために論理的に同時に使用できる場合はグループ モジュール。 たとえば、プログラムのメンテナンスで頻繁に使用される型とクラスで構成されるアセンブリは同じアセンブリに配置することができます。 さらに、複数のアプリケーションで共有する予定の型をアセンブリにグループ化し、そのアセンブリを厳密な名前で署名する必要があります。  
  
-   セキュリティ  
  
     同じセキュリティ アクセス許可が必要な型を含むグループ モジュール。  
  
-   スコープ  
  
     参照可能範囲を同じアセンブリに制限する必要がある型で構成されるグループ モジュール。  
  
 アンマネージ COM アプリケーションで使用できる共通言語ランタイム アセンブリを作成する際は、特別な考慮事項を設定する必要があります。 アンマネージ コードの使用の詳細については、「[COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)   
 [方法: シングルファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)   
 [方法: マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [マルチファイル アセンブリ](../../../docs/framework/app-domains/multifile-assemblies.md)
