---
title: ファイル モードが正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: bccbbbeb79f38790a4664b0152ca3378fb55448d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587385"
---
# <a name="bad-file-mode"></a>ファイル モードが正しくありません。
ファイルの内容を操作するときに使用するステートメントは、ファイルが開かれたモードに対応する必要があります。 以下の原因が考えられます。  
  
-   A`FilePutObject`または`FileGetObject`ステートメントはシーケンシャル ファイルを指定します。  
  
-   A`Print`ステートメント以外の場合、アクセス モードで開かれたファイルを指定する`Output`または`Append`です。  
  
-   `Input`ステートメント以外の場合、アクセス モードで開かれたファイルを指定します `Input`  
  
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
