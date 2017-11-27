---
title: /langversion (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cfe91588471cc8410b25addea8d66a0388c9c5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-visual-basic"></a>/langversion (Visual Basic)
指定された Visual Basic 言語バージョンに含まれている構文のみを受け入れるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a>引数  
 `version`  
 必須です。 コンパイル時に使用する言語バージョン。 指定できる値は`9`、 `9.0`、 `10`、および`10.0`です。  
  
## <a name="remarks"></a>コメント  
 `/langversion`オプションは、コンパイラを受け入れるどのような構文を指定します。 たとえば、言語バージョンを 9.0 を指定する場合、コンパイラは、バージョン 10.0 でのみ有効であり、それ以降は、構文エラーを生成します。  
  
 .NET Framework の異なるバージョンを対象のアプリケーションを開発する場合は、このオプションを使用することができます。 たとえば、.NET Framework 3.5 を対象とする場合は、言語バージョン 10.0 から構文を使用しないことを確認するこのオプションを使用する可能性があります。  
  
 設定することができます`/langversion`直接コマンドラインを使用してのみです。 詳細については、「[対象となる特定の .NET Framework のバージョンの指定](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)」を参照してください。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`sample.vb`Visual Basic 9.0 のです。  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [対象となる特定の .NET Framework バージョンの指定](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
