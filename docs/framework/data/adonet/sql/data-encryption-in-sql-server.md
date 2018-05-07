---
title: SQL Server でのデータの暗号化
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: 9e2924dc9f2f2954f6690ad5009c4143d1b9a44f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="data-encryption-in-sql-server"></a>SQL Server でのデータの暗号化
SQL Server には、証明書、非対称キー、対称キーのいずれかを使ってデータを暗号化したり、復号化したりできる関数が用意されています。 これらはすべて内部の証明書ストアで管理されます。 証明書ストアは、1 つ上の層がその下の層を保護する暗号化階層を使用することによって、証明書およびキーを保護します。 SQL Server では、この機能領域をシークレット ストレージと呼びます。  
  
 暗号化関数によってサポートされる最速の暗号化方式は対称キーによる暗号化です。 この方法は大量のデータを処理する場合に適しています。 対称キーは、証明書、パスワードまたは他の対称キーで暗号化できます。  
  
## <a name="keys-and-algorithms"></a>キーとアルゴリズム  
 SQL Server は、DES、Triple DES、RC2、RC4、128 ビット RC4、DESX、128 ビット AES、192 ビット AES、256 ビット AES など、複数の対称キー暗号化アルゴリズムをサポートしています。 アルゴリズムは Windows Crypto API を使って実装されています。  
  
 SQL Server は、オープンする対称キーをデータベース接続のスコープ内で複数管理できます。 オープンするキーは証明書ストアから取得でき、データを復号化する際に使用できます。 データの一部が復号化されていれば、使用する対称キーを指定する必要はありません。 暗号化された各値は、どのキーを使って暗号化されたかを示すキー識別子 (キー GUID) を保持します。 正しいキーが復号化されてオープンされた場合、暗号化されたバイト ストリームとオープンする対称キーとがエンジンによって照合されます。 次に、このキーを使って復号化が実行されて、データが返されます。 正しいキーがオープンされなかった場合は NULL が返されます。  
  
 例については、データベースの暗号化されたデータを操作する方法を示す、次を参照してください。[する方法: 列のデータを暗号化](http://go.microsoft.com/fwlink/?LinkID=128559)SQL Server オンライン ブック。  
  
## <a name="external-resources"></a>外部リソース  
 データの暗号化の詳細については、次のリソースを参照してください。  
  
|||  
|-|-|  
|[SQL Server の暗号化](http://msdn.microsoft.com/library/bb510663.aspx)SQL Server オンライン ブック|SQL Server における暗号化の概要を説明します。 このトピックには、他のトピックや具体的な方法を示したページへのリンクが用意されています。|  
|[暗号化階層](http://msdn.microsoft.com/library/ms189586.aspx)と[暗号化方法に関するトピック](http://msdn.microsoft.com/library/aa337557.aspx)SQL Server オンライン ブック|SQL Server における暗号化の概要を説明します。 このトピックには、他のトピックや具体的な方法を示したページへのリンクが用意されています。|  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server におけるアプリケーション セキュリティのシナリオ](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server での認証](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [SQL Server のサーバー ロールとデータベース ロール](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [SQL Server における所有権とユーザーとスキーマの分離](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [SQL Server の承認とアクセス許可](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
