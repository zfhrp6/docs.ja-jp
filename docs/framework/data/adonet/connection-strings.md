---
title: "ADO.NET での接続文字列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6737b451a0ccb42dfb83dda487e351a9fafde398
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="connection-strings-in-adonet"></a>ADO.NET での接続文字列
.NET Framework 2.0 では、接続文字列を扱う新しい機能が導入されました。接続文字列ビルダー クラスに追加された新しいキーワードもその 1 つであり、有効な接続文字列を実行時に簡単に作成できるようになっています。  
  
 接続文字列には、データ プロバイダーからデータ ソースにパラメーターとして渡す初期化情報が含まれています。 接続文字列は接続を開くときに解析され、その構文はデータ プロバイダーによって異なります。 構文エラーの場合はランタイム例外が生成されますが、その他のエラーは、データ ソースが接続情報を受け取った後でのみ発生します。 いったん接続文字列が検証されると、接続文字列に指定されたオプションがデータ ソースによって適用されて接続が開かれます。  
  
 接続文字列の形式は、キーと値パラメーターのペアをセミコロンで区切ったリストです。  
  
 `keyword1=value; keyword2=value;`  
  
 キーワードの大文字と小文字は区別されません。また、キーと値のペア間のスペースは無視されます。 ただし、値の大文字と小文字を区別するかどうかはデータ ソースにより異なる場合があります。 値にセミコロン、単一引用符、または二重引用符が含まれている場合は、必ず二重引用符で囲む必要があります。  
  
 有効な接続文字列の構文はプロバイダーによって異なり、ODBC のような初期の API から長年にわたって進化しています。 .NET Framework Data Provider for SQL Server (SqlClient) には、古い構文の要素が多数組み込まれており、一般的に、共通の接続文字列の構文に対しては柔軟性があります。 多くの場合、接続文字列の構文要素には同等として扱われる有効なシノニムが存在しますが、構文やスペルの誤りによって問題が生じる場合もあります。 たとえば、"`Integrated Security=true`" は有効ですが、"`IntegratedSecurity=true`" ではエラーが発生します。 また、ユーザー入力を基にして接続文字列を実行時に構築する場合、入力された文字列を検証しないと、文字列のインジェクション攻撃を招き、データ ソースのセキュリティが脅かされる可能性があります。  
  
 こうした問題に対処するため、ADO.NET 2.0 では、各 .NET Framework データ プロバイダー用の新しい接続文字列ビルダーが導入されました。 キーワードがプロパティとして公開され、接続文字列をデータ ソースに送信する前に、その構文を検証できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 `ConnectionStringBuilder` クラスを使用して、有効な接続文字列を実行時に作成する方法について説明します。  
  
 [接続文字列と構成ファイル](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 構成ファイルを使用した接続文字列の格納と取得の方法について説明します。  
  
 [接続文字列の構文](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 `SqlClient`、`OracleClient`、`OleDb`、`Odbc` の各プロバイダーに固有の接続文字列を構成する方法について説明します。  
  
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 データ ソースへの接続に使用する情報を保護する方法を示します。  
  
## <a name="see-also"></a>参照  
 [データ ソースへの接続](/cpp/data/odbc/connecting-to-a-data-source)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
