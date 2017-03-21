---
title: "/langversion (Visual Basic) |Microsoft ドキュメント"
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
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: 8
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
ms.openlocfilehash: 9970df0c9babc368210169fae0490b423d77f40d
ms.lasthandoff: 03/13/2017

---
# <a name="langversion-visual-basic"></a>/langversion (Visual Basic)
コンパイラが指定された Visual Basic の言語バージョンに含まれている構文のみを受け入れるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a>引数  
 `version`  
 必須です。 コンパイル時に使用する言語バージョン。 許容値は`9`、 `9.0`、 `10`、および`10.0`です。  
  
## <a name="remarks"></a>コメント  
 `/langversion`オプションは、コンパイラはどのような構文を指定します。 たとえば、9.0 インストールされている言語バージョンを指定する場合、コンパイラは、バージョン 10.0 でのみ有効ですし、後では、構文のエラーを生成します。  
  
 .NET Framework の異なるバージョンを対象のアプリケーションを開発する場合は、このオプションを使用することができます。 たとえば、.NET Framework 3.5 を対象とする場合は、言語バージョン 10.0 から構文を使用しないことを確認するこのオプションを使用する可能性があります。  
  
 設定する`/langversion`直接、コマンドラインを使用してのみです。 詳細については、「[対象となる特定の .NET Framework のバージョンの指定](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)」を参照してください。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`sample.vb`Visual Basic 9.0 のです。  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [対象となる特定の .NET Framework バージョンの指定](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
