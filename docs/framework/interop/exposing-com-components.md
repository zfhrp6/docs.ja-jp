---
title: ".NET Framework への COM コンポーネントの公開 | Microsoft Docs"
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
  - "COM 相互運用機能, 公開 (COM コンポーネントを)"
  - "公開 (.NET Framework に COM コンポーネントを)"
  - "相互運用 (アンマネージ コードとの), 公開 (COM コンポーネントを)"
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# .NET Framework への COM コンポーネントの公開
このセクションでは、既存の COM コンポーネントをマネージ コードに公開するために必要な処理について要約します。  .NET Framework と緊密に統合された COM サーバーの詳細については、「[相互運用のためのデザインの考慮事項](http://msdn.microsoft.com/ja-jp/b59637f6-fe35-40d6-ae72-901e7a707689)」を参照してください。  
  
 既存の COM コンポーネントは、中間層のビジネス アプリケーションや独立の機能として、マネージ コードでは貴重なリソースとなります。  プライマリ相互運用機能アセンブリを持ち、COM のプログラミング標準に厳密に準拠したコンポーネントが理想的なコンポーネントです。  
  
#### .NET Framework に COM コンポーネントを公開するには  
  
1.  [タイプ ライブラリのアセンブリとしてのインポート](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
  
     共通言語ランタイムでは、COM 型を含め、すべての型についてメタデータが必要です。  メタデータとしてインポートされた COM 型を含んだアセンブリを取得するには、いくつかの方法があります。  
  
2.  [マネージ コード内で COM 型を作成します](http://msdn.microsoft.com/ja-jp/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)。  
  
     通常のマネージ型の場合と同様の方法で、COM 型を検査したり、インスタンスをアクティブにしたり、COM オブジェクトのメソッドを呼び出したりできます。  
  
3.  [相互運用プロジェクトをコンパイルします](../../../docs/framework/interop/compiling-an-interop-project.md)。  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] には、[!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C\#、C\+\+ など、共通言語仕様 \(CLS: Common Language Specification\) に準拠した複数の言語用のコンパイラが用意されています。  
  
4.  [相互運用アプリケーションを配置します](../../../docs/framework/interop/deploying-an-interop-application.md)。  
  
     相互運用アプリケーションは、[厳密な名前](../../../docs/framework/app-domains/strong-named-assemblies.md)が付けられた署名済みアセンブリとして、グローバル アセンブリ キャッシュに配置することをお勧めします。  
  
## 参照  
 [アンマネージ コードとの相互運用](../../../docs/framework/interop/index.md)   
 [Design Considerations for Interoperation](http://msdn.microsoft.com/ja-jp/b59637f6-fe35-40d6-ae72-901e7a707689)   
 [COM 相互運用機能のサンプル: .NET クライアントおよび COM サーバー](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)   
 [言語への非依存性、および言語非依存コンポーネント](../../../docs/standard/language-independence-and-language-independent-components.md)   
 [Gacutil.exe \(グローバル アセンブリ キャッシュ ツール\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)