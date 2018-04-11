---
title: ファイル モードが正しくありません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a>ファイル モードが正しくありません。
ファイルの内容を操作するときに使用するステートメントは、ファイルが開かれたモードに対応する必要があります。 以下の原因が考えられます。  
  
-   A`FilePutObject`または`FileGetObject`ステートメントはシーケンシャル ファイルを指定します。  
  
-   A`Print`ステートメント以外の場合、アクセス モードで開かれたファイルを指定する`Output`または`Append`です。  
  
-   `Input`ステートメント以外の場合、アクセス モードで開かれたファイルを指定します`Input`  
  
-   読み取り専用ファイルに書き込もうとしています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   確認してください`FilePutObject`と`FileGetObject`の開いているファイルだけが参照され`Random`または`Binary`アクセスします。  
  
-   確認`Print`のいずれかで開かれるファイルを指定`Output`または`Append`アクセス モードです。 ない場合は、さまざまなステートメントを使用して、データ ファイル内に配置または適切なモードでファイルを閉じて再度開きます。  
  
-   確認`Input`で開いたファイルを指定`Input`です。 それ以外の場合は、さまざまなステートメントを使用して、データ ファイル内に配置または適切なモードでファイルを閉じて再度開きます。  
  
-   読み取り専用ファイルに書き込みを行う場合は、ファイルの読み取り/書き込み状態を変更したりへの書き込みをしないでください。  
  
-   `My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [トラブルシューティング : テキスト ファイルの読み取りと書き込み](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
