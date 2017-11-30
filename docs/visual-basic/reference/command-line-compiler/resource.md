---
title: /resource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 858a216873ad9999722388e45d5de28398b27fbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="resource-visual-basic"></a>/resource (Visual Basic)
マネージ リソースをアセンブリに埋め込みます。  
  
## <a name="syntax"></a>構文  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`filename`|必須です。 出力ファイルに埋め込むには、リソース ファイルの名前。 既定では、`filename`がアセンブリに公開します。 ファイル名を引用符で囲みます ("")、スペースが含まれている場合。|  
|`identifier`|省略可能です。 リソースの論理名ファイルを読み込むための名前。 既定値は、ファイルの名前です。 かどうか、リソースは、パブリックまたはプライベート アセンブリ マニフェストとに、次を指定することができます必要に応じて、: `/res:``filename.res`、`myname.res`、`public`|  
  
## <a name="remarks"></a>コメント  
 使用して`/linkresource`出力ファイルにリソース ファイルを配置することがなく、アセンブリにリソースをリンクします。  
  
 場合`filename`は、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]作成されたリソース ファイル、たとえば、によって、 [Resgen.exe (リソース ファイル ジェネレーター)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)または開発環境でアクセスできるメンバー間で、<xref:System.Resources>名前空間 (参照<xref:System.Resources.ResourceManager>詳細については)。 実行時にその他のすべてのリソースにアクセスするには、次のいずれかを使用: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>、 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>、または<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>です。  
  
 `/resource` の省略形は `/res` です。  
  
 設定する方法については`/resource`Visual Studio IDE で、次を参照してください。[を管理するアプリケーションのリソース (.NET)](/visualstudio/ide/managing-application-resources-dotnet)です。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`とアタッチのリソース ファイル`Rf.resource`です。  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
