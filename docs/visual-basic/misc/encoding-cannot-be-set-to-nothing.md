---
title: エンコードは Nothing に設定できません
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 05f64dfe9610f679986040ec87e6287caac9bd08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33638121"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>エンコードは Nothing に設定できません
パラメーター `encoding` が `Nothing` に設定されていますが、正しい値が必要なため、ファイルへの読み取りまたは書き込みに失敗しました。  
  
 <xref:System.Text.Encoding> は、ファイルへの書き込み時に使用するエンコードを判別するのに使用されます。 既定は UTF-8 です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   正しい値を `encoding` パラメーターに指定します。  
  
## <a name="see-also"></a>関連項目  
 [ファイル エンコーディング](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 [ファイルの読み取り](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [ファイルへの書き込み](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)  
 [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
