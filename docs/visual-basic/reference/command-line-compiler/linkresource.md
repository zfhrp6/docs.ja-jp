---
title: "/linkresource (Visual Basic) |Microsoft ドキュメント"
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
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fafde6563340189108a879b82e7e880aca690b39
ms.lasthandoff: 03/13/2017

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
 省略可能です。 リソースの論理名。 リソースを読み込むために使用される名前です。 既定では、ファイルの名前です。 必要に応じてを指定できるかどうか、ファイルがパブリックかプライベート アセンブリ マニフェストの例:`/linkres:filename.res,myname.res,public`です。 既定では、`filename`はアセンブリ内でパブリックです。  
  
## <a name="remarks"></a>コメント  
 `/linkresource`オプションで、出力ファイルのリソース ファイルが埋め込まれません。 を使用して、`/resource`これを行うオプションです。  
  
 `/linkresource`オプションでは、いずれかが必要です、`/target`以外のオプション`/target:module`します。  
  
 場合`filename`は、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイルの作成例についてで、 [Resgen.exe (リソース ファイル ジェネレーター)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)または開発環境でアクセスできるメンバー間で、<xref:System.Resources>名前空間</xref:System.Resources>。 (詳細については、次を参照してください<xref:System.Resources.ResourceManager>。)</xref:System.Resources.ResourceManager> 。実行時にその他のすべてのリソースにアクセスするで始まるメソッドを使用して`GetManifestResource`<xref:System.Reflection.Assembly>クラス</xref:System.Reflection.Assembly>の  
  
 ファイル名には、任意のファイル形式を指定できます。 たとえば、ネイティブの DLL が、アセンブリの一部は、グローバル アセンブリ キャッシュにインストールされているし、アセンブリ内のマネージ コードからアクセスできるようにすることがあります。  
  
 短い形式の`/linkresource`は`/linkres`です。  
  
> [!NOTE]
>  `/linkresource`オプションは、Visual Studio 開発環境からは使用できません。 は、コマンドラインからコンパイルする場合のみです。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`とリソース ファイルへのリンク`Rf.resource`します。  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
