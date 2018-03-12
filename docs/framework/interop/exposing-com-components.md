---
title: ".NET Framework への COM コンポーネントの公開"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2a73bbe23cc1e8fd267489d2607dd7275b09322
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="exposing-com-components-to-the-net-framework"></a>.NET Framework への COM コンポーネントの公開
このセクションでは、既存の COM コンポーネントをマネージ コードに公開するために必要なプロセスをまとめています。 .NET Framework と緊密に統合される COM サーバーの詳細については、「[Design Considerations for Interoperation](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))」(相互運用のためのデザインの考慮事項) を参照してください。
  
 既存の COM コンポーネントは、中間層のビジネス アプリケーション、または独立した機能として、マネージ コードでの貴重なリソースです。 理想的なコンポーネントは、プライマリ相互運用機能アセンブリがあり、COM で課せられるプログラミング標準に厳密に準拠しています。  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>.NET Framework に COM コンポーネントを公開するには  
  
1.  [タイプ ライブラリをアセンブリとしてインポートする](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)。  
  
     共通言語ランタイムでは、COM 型を含め、すべてのタイプにメタデータが必要です。 メタデータとしてインポートされた COM 型を含むアセンブリを取得するには、複数の方法があります。  
  
2.  [マネージ コードで COM 型を作成する](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))。  
  
     任意のマネージ型で行うのと同じ方法で、COM オブジェクトで COM 型の検査、インスタンスのアクティブ化、およびメソッドの呼び出しができます。  
  
3.  [相互運用プロジェクトをコンパイルする](../../../docs/framework/interop/compiling-an-interop-project.md)。  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] では、共通言語仕様 (CLS) に準拠する複数の言語 ([!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C#、C++ など) のコンパイラが用意されています。  
  
4.  [相互運用アプリケーションを展開する](../../../docs/framework/interop/deploying-an-interop-application.md)。  
  
     相互運用アプリケーションは、[厳密な名前を付けた](../../../docs/framework/app-domains/strong-named-assemblies.md)、署名されたアセンブリとして、グローバル アセンブリ キャッシュに最適に展開されます。  
  
## <a name="see-also"></a>参照  
 [アンマネージ コードとの相互運用](../../../docs/framework/interop/index.md)  
 [相互運用のためのデザインの考慮事項](http://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689)  
 [COM 相互運用機能のサンプル: .NET クライアントおよび COM サーバー](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)  
 [言語への非依存性、および言語非依存コンポーネント](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
