---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a>/linkresource (Visual Basic)
マネージ リソースへのリンクを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 必須です。 アセンブリにリンクするリソース ファイル。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。  
  
 `identifier`  
 省略可能です。 リソースの論理名。 リソースの読み込みに使用される名前です。 既定値は、ファイルの名前です。 かどうか、ファイルがパブリックかプライベート アセンブリ マニフェストに例を指定することができます必要に応じて、:`/linkres:filename.res,myname.res,public`です。 既定では、`filename`がアセンブリに公開します。  
  
## <a name="remarks"></a>コメント  
 `/linkresource`オプションは、リソース ファイルを出力ファイルに埋め込まれません。 を使用して、`/resource`これを行うオプション。  
  
 `/linkresource`オプションでは、いずれかが必要です、`/target`以外のオプション`/target:module`です。  
  
 場合`filename`は、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]作成されたリソース ファイル、たとえば、によって、 [Resgen.exe (リソース ファイル ジェネレーター)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)または開発環境でアクセスできるメンバー間で、<xref:System.Resources>名前空間。 (詳細については、「<xref:System.Resources.ResourceManager>」を参照してください)。実行時にその他のすべてのリソースにアクセスするで始まるメソッドを使用して`GetManifestResource`で、<xref:System.Reflection.Assembly>クラスです。  
  
 ファイル名には、任意のファイル形式を指定できます。 たとえば、ネイティブ DLL をアセンブリの一部にすることで、グローバル アセンブリ キャッシュにインストールして、アセンブリ内のマネージ コードからアクセスできるようにすることができます。  
  
 `/linkresource` の省略形は `/linkres` です。  
  
> [!NOTE]
>  `/linkresource`オプションは、Visual Studio 開発環境からは使用できません。 使用可能なコマンドラインからコンパイルするときにのみです。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`とリソース ファイルへのリンク`Rf.resource`です。  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
