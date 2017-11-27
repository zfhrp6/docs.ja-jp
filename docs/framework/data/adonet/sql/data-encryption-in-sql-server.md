---
title: "SQL Server でのデータの暗号化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4428cf8fbfcaa853ca2c877a8cc4902f585b6754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="data-encryption-in-sql-server"></a><span data-ttu-id="a460e-102">SQL Server でのデータの暗号化</span><span class="sxs-lookup"><span data-stu-id="a460e-102">Data Encryption in SQL Server</span></span>
<span data-ttu-id="a460e-103">SQL Server には、証明書、非対称キー、対称キーのいずれかを使ってデータを暗号化したり、復号化したりできる関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a460e-103">SQL Server provides functions to encrypt and decrypt data using a certificate, asymmetric key, or symmetric key.</span></span> <span data-ttu-id="a460e-104">これらはすべて内部の証明書ストアで管理されます。</span><span class="sxs-lookup"><span data-stu-id="a460e-104">It manages all of these in an internal certificate store.</span></span> <span data-ttu-id="a460e-105">証明書ストアは、1 つ上の層がその下の層を保護する暗号化階層を使用することによって、証明書およびキーを保護します。</span><span class="sxs-lookup"><span data-stu-id="a460e-105">The store uses an encryption hierarchy that secures certificates and keys at one level with the layer above it in the hierarchy.</span></span> <span data-ttu-id="a460e-106">SQL Server では、この機能領域をシークレット ストレージと呼びます。</span><span class="sxs-lookup"><span data-stu-id="a460e-106">This feature area of SQL Server is called Secret Storage.</span></span>  
  
 <span data-ttu-id="a460e-107">暗号化関数によってサポートされる最速の暗号化方式は対称キーによる暗号化です。</span><span class="sxs-lookup"><span data-stu-id="a460e-107">The fastest mode of encryption supported by the encryption functions is symmetric key encryption.</span></span> <span data-ttu-id="a460e-108">この方法は大量のデータを処理する場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="a460e-108">This mode is suitable for handling large volumes of data.</span></span> <span data-ttu-id="a460e-109">対称キーは、証明書、パスワードまたは他の対称キーで暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="a460e-109">The symmetric keys can be encrypted by certificates, passwords or other symmetric keys.</span></span>  
  
## <a name="keys-and-algorithms"></a><span data-ttu-id="a460e-110">キーとアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="a460e-110">Keys and Algorithms</span></span>  
 <span data-ttu-id="a460e-111">SQL Server は、DES、Triple DES、RC2、RC4、128 ビット RC4、DESX、128 ビット AES、192 ビット AES、256 ビット AES など、複数の対称キー暗号化アルゴリズムをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a460e-111">SQL Server supports several symmetric key encryption algorithms, including DES, Triple DES, RC2, RC4, 128-bit RC4, DESX, 128-bit AES, 192-bit AES, and 256-bit AES.</span></span> <span data-ttu-id="a460e-112">アルゴリズムは Windows Crypto API を使って実装されています。</span><span class="sxs-lookup"><span data-stu-id="a460e-112">The algorithms are implemented using the Windows Crypto API.</span></span>  
  
 <span data-ttu-id="a460e-113">SQL Server は、オープンする対称キーをデータベース接続のスコープ内で複数管理できます。</span><span class="sxs-lookup"><span data-stu-id="a460e-113">Within the scope of a database connection, SQL Server can maintain multiple open symmetric keys.</span></span> <span data-ttu-id="a460e-114">オープンするキーは証明書ストアから取得でき、データを復号化する際に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a460e-114">An open key is retrieved from the store and is available for decrypting data.</span></span> <span data-ttu-id="a460e-115">データの一部が復号化されていれば、使用する対称キーを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a460e-115">When a piece of data is decrypted, there is no need to specify the symmetric key to use.</span></span> <span data-ttu-id="a460e-116">暗号化された各値は、どのキーを使って暗号化されたかを示すキー識別子 (キー GUID) を保持します。</span><span class="sxs-lookup"><span data-stu-id="a460e-116">Each encrypted value contains the key identifier (key GUID) of the key used to encrypt it.</span></span> <span data-ttu-id="a460e-117">正しいキーが復号化されてオープンされた場合、暗号化されたバイト ストリームとオープンする対称キーとがエンジンによって照合されます。</span><span class="sxs-lookup"><span data-stu-id="a460e-117">The engine matches the encrypted byte stream to an open symmetric key, if the correct key has been decrypted and is open.</span></span> <span data-ttu-id="a460e-118">次に、このキーを使って復号化が実行されて、データが返されます。</span><span class="sxs-lookup"><span data-stu-id="a460e-118">This key is then used to perform decryption and return the data.</span></span> <span data-ttu-id="a460e-119">正しいキーがオープンされなかった場合は NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="a460e-119">If the correct key is not open, NULL is returned.</span></span>  
  
 <span data-ttu-id="a460e-120">例については、データベースの暗号化されたデータを操作する方法を示す、次を参照してください。[する方法: 列のデータを暗号化](http://go.microsoft.com/fwlink/?LinkID=128559)SQL Server オンライン ブック。</span><span class="sxs-lookup"><span data-stu-id="a460e-120">For an example that shows how to work with encrypted data in a database, see [How to: Encrypt a Column of Data](http://go.microsoft.com/fwlink/?LinkID=128559) in SQL Server Books Online.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="a460e-121">外部リソース</span><span class="sxs-lookup"><span data-stu-id="a460e-121">External Resources</span></span>  
 <span data-ttu-id="a460e-122">データの暗号化の詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a460e-122">For more information on data encryption, see the following resources.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a460e-123">[SQL Server の暗号化](http://msdn.microsoft.com/library/bb510663.aspx)SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="a460e-123">[SQL Server Encryption](http://msdn.microsoft.com/library/bb510663.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="a460e-124">SQL Server における暗号化の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="a460e-124">Provides an overview of encryption in SQL Serve.</span></span> <span data-ttu-id="a460e-125">このトピックには、他のトピックや具体的な方法を示したページへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a460e-125">This topic includes links to additional topics and how-to's.</span></span>|  
|<span data-ttu-id="a460e-126">[暗号化階層](http://msdn.microsoft.com/library/ms189586.aspx)と[暗号化方法に関するトピック](http://msdn.microsoft.com/library/aa337557.aspx)SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="a460e-126">[Encryption Hierarchy](http://msdn.microsoft.com/library/ms189586.aspx) and [Encryption How-to Topics](http://msdn.microsoft.com/library/aa337557.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="a460e-127">SQL Server における暗号化の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="a460e-127">Provides an overview of encryption in SQL Server.</span></span> <span data-ttu-id="a460e-128">このトピックには、他のトピックや具体的な方法を示したページへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a460e-128">This topic provides links to additional topics and how-to's.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a460e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a460e-129">See Also</span></span>  
 [<span data-ttu-id="a460e-130">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="a460e-130">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="a460e-131">SQL Server におけるアプリケーション セキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="a460e-131">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="a460e-132">SQL Server での認証</span><span class="sxs-lookup"><span data-stu-id="a460e-132">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [<span data-ttu-id="a460e-133">サーバーと SQL server データベース ロール</span><span class="sxs-lookup"><span data-stu-id="a460e-133">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [<span data-ttu-id="a460e-134">所有権と SQL Server のユーザーとスキーマの分離</span><span class="sxs-lookup"><span data-stu-id="a460e-134">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [<span data-ttu-id="a460e-135">SQL Server の承認と権限</span><span class="sxs-lookup"><span data-stu-id="a460e-135">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [<span data-ttu-id="a460e-136">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="a460e-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
