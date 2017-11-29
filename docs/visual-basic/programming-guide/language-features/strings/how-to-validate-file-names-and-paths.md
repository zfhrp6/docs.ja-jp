---
title: "方法 : Visual Basic でファイル名とパスを検証する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c50d09dd7160992ffd95ececeff623a8aa93d2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>方法 : Visual Basic でファイル名とパスを検証する
この例を返します、`Boolean`文字列が、ファイル名またはパスを表すかどうかを示す値。 検証では、名前に、ファイル システムで許可されない文字が含まれるかどうかを確認します。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 この例では、名前の位置が正しくないコロン、またはディレクトリ名がない場合、または名の長さがシステム定義の最大長を超える場合はチェックしません。 または確認しません、アプリケーションが、指定した名前のファイル システム リソースにアクセスする権限を持つかどうかです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
