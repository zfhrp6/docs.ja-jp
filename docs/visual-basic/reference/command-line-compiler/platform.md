---
title: /platform (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d52ade26bc249625a77720fe05ad9c1ab58b04f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="platform-visual-basic"></a>/platform (Visual Basic)
出力ファイルをどのプラットフォーム用の共通言語ランタイム (CLR) で実行するかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`x86`|32 ビット x86 互換 CLR で実行されるように、アセンブリをコンパイルします。|  
|`x64`|AMD64 または EM64T 命令セットをサポートするコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。|  
|`Itanium`|Itanium プロセッサ搭載のコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。|  
|`arm`|ARM (アドバンスト RISC マシン) プロセッサ搭載のコンピューター上で実行されるように、アセンブリをコンパイルします。|  
|`anycpu`|任意のプラットフォーム上で実行されるように、アセンブリをコンパイルします。 アプリケーションは、Windows の 32 ビット バージョンでは 32 ビット アプリケーションとして、Windows の 64 ビット バージョンでは 64 ビット アプリケーションとして実行されます。 このフラグが既定値です。|  
|`anycpu32bitpreferred`|任意のプラットフォーム上で実行されるように、アセンブリをコンパイルします。 アプリケーションは、Windows の 32 ビット バージョンおよび 64 ビット バージョンの両方で、 32 ビット アプリケーションとして実行されます。 このフラグは、実行可能ファイル (.EXE) に対してのみ有効であり、[!INCLUDE[net_v45](~/includes/net-v45-md.md)] を要求します。|  
  
## <a name="remarks"></a>コメント  
 出力ファイルの対象となるプロセッサの種類を指定するには、`/platform` オプションを使用します。  
  
 通常、Visual Basic で記述された .NET Framework アセンブリは、プラットフォームに関係なく、同じように実行されます。 ただし、プラットフォーム間で動作が異なる場合があります。 その一般的な例を次に示します。  
  
-   プラットフォームによってメンバーのサイズが変わる構造体 (ポインター型など)  
  
-   定数のサイズを含むポインター演算  
  
-   ハンドルに `Integer` ではなく <xref:System.IntPtr> を使用した不適切なプラットフォーム呼び出しまたは COM 宣言  
  
-   <xref:System.IntPtr> の `Integer` へのキャスト  
  
-   すべてのプラットフォームに存在するとは限らないコンポーネントを使用したプラットフォーム呼び出しまたは COM 相互運用機能の使用  
  
 **/Platform**でコードが実行されるアーキテクチャに関する前提条件を行ったことがわかっている場合、オプションがいくつかの問題が軽減されます。 具体的には、次のように使用します。  
  
-   64 ビット プラットフォームを対象にし、アプリケーションを 32 ビット マシンで実行した場合、エラー メッセージは、このスイッチを使用しない場合よりも、エラー メッセージがかなり早期に出力され、より絞り込まれた内容になります。  
  
-   オプションに `x86` フラグを設定し、その後、アプリケーションを 64 ビット マシンで実行した場合、アプリケーションはネイティブに実行されず、WOW サブシステムで実行されます。  
  
 64 ビット Windows オペレーティング システムの場合:  
  
-   `/platform:x86` でコンパイルされたアセンブリは、WOW64 の下で動作する 32 ビット CLR で実行されます。  
  
-   `/platform:anycpu` でコンパイルされた実行可能ファイルは、64 ビット CLR で実行されます。  
  
-   `/platform:anycpu` でコンパイルでされた DLL は、ロード先のプロセスと同じ CLR で実行されます。  
  
-   `/platform:anycpu32bitpreferred` でコンパイルされた実行可能ファイルは、32 ビット CLR で実行されます。  
  
 64 ビット バージョンの Windows で実行するアプリケーションを開発する方法の詳細については、次を参照してください。 [64 ビット アプリケーション](https://msdn.microsoft.com/library/ms241064)です。  
  
### <a name="to-set-platform-in-the-visual-studio-ide"></a>Visual Studio IDE で /platform を設定するには  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを選択を開く、**プロジェクト** メニューをクリックして**プロパティ**です。  
  
     詳細については、次を参照してください。 [NIB: プロジェクト デザイナーでプロジェクトのプロパティを管理する](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)です。  
  
2.  **コンパイル** タブ、オンまたはオフ、**必要に応じて 32 ビット** チェック ボックスまたは、**ターゲット CPU**一覧で、値を選択します。  
  
     詳細については、次を参照してください。[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)です。  
  
## <a name="example"></a>例  
 次の例は、`/platform` コンパイラ オプションを使用する方法を示しています。  
  
```  
vbc /platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [/target (Visual Basic)](target.md)  
 [Visual Basic のコマンド ライン コンパイラ](index.md)  
 [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
