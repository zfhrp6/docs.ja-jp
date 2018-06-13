---
title: '方法 : Visual Basic でファイル名とパスを検証する'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: ab3df335bc5bba21d386bb69b12d840990e629fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647805"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>方法 : Visual Basic でファイル名とパスを検証する
この例を返します、`Boolean`文字列が、ファイル名またはパスを表すかどうかを示す値。 検証では、名前に、ファイル システムで許可されない文字が含まれるかどうかを確認します。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 この例では、名前の位置が正しくないコロン、またはディレクトリ名がない場合、または名の長さがシステム定義の最大長を超える場合はチェックしません。 または確認しません、アプリケーションが、指定した名前のファイル システム リソースにアクセスする権限を持つかどうかです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
