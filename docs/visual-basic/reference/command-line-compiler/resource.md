---
title: "/resource (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b46800322fd03eb2578cc558cc1d9bb78550aa61
ms.lasthandoff: 03/13/2017

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
|`filename`|必須です。 出力ファイルに埋め込まれるリソース ファイルの名前。 既定では、`filename`はアセンブリ内でパブリックです。 ファイル名を引用符で囲みます ("")、スペースが含まれている場合。|  
|`identifier`|省略可能です。 リソースの論理名それを読み込むために使用する名前です。 既定では、ファイルの名前です。 同様に、次が、パブリックまたはプライベート アセンブリ マニフェスト内にリソースかどうかを指定できます必要に応じて、: `/res:``filename.res`、`myname.res`、`public`|  
  
## <a name="remarks"></a>コメント  
 使用`/linkresource`出力ファイルにリソース ファイルをかけることがなく、アセンブリにリソースをリンクします。  
  
 場合`filename`は、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイルの作成例についてで、 [Resgen.exe (リソース ファイル ジェネレーター)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)または開発環境でアクセスできるメンバー間で、<xref:System.Resources>名前空間 (を参照してください<xref:System.Resources.ResourceManager>の詳細).</xref:System.Resources.ResourceManager> </xref:System.Resources> 実行時にその他のすべてのリソースにアクセスするには、次のいずれかを使用します<xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>、 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>、または<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</xref:System.Reflection.Assembly.GetManifestResourceStream%2A> </xref:System.Reflection.Assembly.GetManifestResourceNames%2A> </xref:System.Reflection.Assembly.GetManifestResourceInfo%2A> 。  
  
 短い形式の`/resource`は`/res`です。  
  
 設定する方法については`/resource`Visual Studio ide では、次を参照してください。[を管理するアプリケーションのリソース (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`とアタッチのリソース ファイル`Rf.resource`します。  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)   
 [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
