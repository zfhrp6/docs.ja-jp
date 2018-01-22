---
title: "相互運用プロジェクトのコンパイル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1668961e383532de832b538e57eedb681a26ed52
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="compiling-an-interop-project"></a>相互運用プロジェクトのコンパイル
インポートされた COM 型を含む 1 つ以上のアセンブリを参照する COM 相互運用プロジェクトは、他のマネージ プロジェクトと同じようにコンパイルされます。 相互運用機能アセンブリは、Visual Studio などの開発環境で参照できます。コマンド ライン コンパイラを使用して参照することもできます。 どちらの場合でも、正常にコンパイルするには、相互運用機能アセンブリを、その他のプロジェクト ファイルと同じディレクトリに配置する必要があります。  
  
 相互運用機能アセンブリを参照する方法には、次の 2 つがあります。  
  
-   埋め込まれた相互運用機能型: [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] および [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 以降では、相互運用機能アセンブリから実行可能ファイルに型情報を埋め込むようにコンパイラに指示できます。 この手法を使用することをお勧めします。  
  
-   相互運用機能アセンブリの配置: 相互運用機能アセンブリへの標準の参照を作成できます。 この場合、アプリケーションで相互運用機能アセンブリを配置する必要があります。  
  
 この 2 つの手法の違いの詳細については、「[Using COM Types in Managed Code](http://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)」(マネージ コードでの COM 型の使用) を参照してください。  
  
 Visual Studio での相互運用機能型の埋め込みについては、「[チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み (C# および Visual Basic)](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)」および「[チュートリアル: マネージ アセンブリからの型の埋め込み (C# および Visual Basic)](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)」を参照してください。  
  
 コマンド ライン コンパイラを使用して相互運用機能アセンブリを参照し、実行可能ファイルに型情報を埋め込むには、[/link (C# コンパイラ オプション)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) または [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) コンパイラ スイッチを使用して、相互運用機能アセンブリの名前を指定します。  
  
> [!NOTE]
>  Visual C++ アプリケーションは型情報を埋め込むことはできませんが、型情報を埋め込むことができるアプリケーションまたはアドインと相互運用できます。  
  
 配置時にプライマリ相互運用機能アセンブリを含むアプリケーションをコンパイルするには、**/reference** コンパイラ スイッチを使用して、相互運用機能アセンブリの名前を指定します。  
  
## <a name="see-also"></a>参照  
 [.NET Framework への COM コンポーネントの公開](../../../docs/framework/interop/exposing-com-components.md)  
 [言語への非依存性、および言語非依存コンポーネント](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [マネージ コードの COM 型の使用](http://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [チュートリアル: マネージ アセンブリからの型の埋め込み](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [タイプ ライブラリのアセンブリとしてのインポート](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
