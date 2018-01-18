---
title: "SQL Server でのストアド プロシージャの署名"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a3f1ed66ed7caf2272ca27097dc9a838bec7d0ae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="signing-stored-procedures-in-sql-server"></a><span data-ttu-id="7535e-102">SQL Server でのストアド プロシージャの署名</span><span class="sxs-lookup"><span data-stu-id="7535e-102">Signing Stored Procedures in SQL Server</span></span>
<span data-ttu-id="7535e-103">証明書や非対称キーを使用してストアド プロシージャに署名することができます。</span><span class="sxs-lookup"><span data-stu-id="7535e-103">You can sign a stored procedure with a certificate or an asymmetric key.</span></span> <span data-ttu-id="7535e-104">この機能は、動的 SQL などのように、組み合わせ所有権によって権限を継承できない場合や、組み合わせ所有権が壊れている場合を想定して用意されています。</span><span class="sxs-lookup"><span data-stu-id="7535e-104">This is designed for scenarios when permissions cannot be inherited through ownership chaining or when the ownership chain is broken, such as dynamic SQL.</span></span> <span data-ttu-id="7535e-105">証明書に割り当てられたユーザーを作成し、その証明書ユーザーにストアド プロシージャがアクセスする必要があるオブジェクトへの権限を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="7535e-105">You then create a user mapped to the certificate, granting the certificate user permissions on the objects the stored procedure needs to access.</span></span>  
  
 <span data-ttu-id="7535e-106">ストアド プロシージャが実行されると、証明書ユーザーの権限が呼び出し元の権限と組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="7535e-106">When the stored procedure is executed, SQL Server combines the permissions of the certificate user with those of the caller.</span></span> <span data-ttu-id="7535e-107">EXECUTE AS 句とは異なり、プロシージャの実行コンテキストは変更されません。</span><span class="sxs-lookup"><span data-stu-id="7535e-107">Unlike the EXECUTE AS clause, it does not change the execution context of the procedure.</span></span> <span data-ttu-id="7535e-108">ログイン名とユーザー名を返す組み込み関数を実行すると、証明書ユーザーの名前ではなく、呼び出し元の名前が返されます。</span><span class="sxs-lookup"><span data-stu-id="7535e-108">Built-in functions that return login and user names return the name of the caller, not the certificate user name.</span></span>  
  
 <span data-ttu-id="7535e-109">デジタル署名は、署名者の秘密キーで暗号化されたデータ ダイジェストです。</span><span class="sxs-lookup"><span data-stu-id="7535e-109">A digital signature is a data digest encrypted with the private key of the signer.</span></span> <span data-ttu-id="7535e-110">秘密キーにより、デジタル署名がその保持者または所有者に固有であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="7535e-110">The private key ensures that the digital signature is unique to its bearer or owner.</span></span> <span data-ttu-id="7535e-111">ストアド プロシージャ、関数、またはトリガーに署名することができます。</span><span class="sxs-lookup"><span data-stu-id="7535e-111">You can sign stored procedures, functions, or triggers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7535e-112">マスター データベースに証明書を作成することで、サーバー レベルの権限を許可できます。</span><span class="sxs-lookup"><span data-stu-id="7535e-112">You can create a certificate in the master database to grant server-level permissions.</span></span>  
  
## <a name="creating-certificates"></a><span data-ttu-id="7535e-113">証明書の作成</span><span class="sxs-lookup"><span data-stu-id="7535e-113">Creating Certificates</span></span>  
 <span data-ttu-id="7535e-114">証明書を使用してストアド プロシージャに署名すると、ストアド プロシージャのコードの暗号化ハッシュで構成されたデータ ダイジェストが秘密キーを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="7535e-114">When you sign a stored procedure with a certificate, a data digest consisting of the encrypted hash of the stored procedure code is created using the private key.</span></span> <span data-ttu-id="7535e-115">実行時に、このデータ ダイジェストが公開キーを使用して復号化され、ストアド プロシージャのハッシュ値と比較されます。</span><span class="sxs-lookup"><span data-stu-id="7535e-115">At run time, the data digest is decrypted with the public key and compared with the hash value of the stored procedure.</span></span> <span data-ttu-id="7535e-116">ストアド プロシージャに変更が加えられるとハッシュ値が無効になり、デジタル署名が一致しなくなります。</span><span class="sxs-lookup"><span data-stu-id="7535e-116">Modifying the stored procedure invalidates the hash value so that the digital signature no longer matches.</span></span> <span data-ttu-id="7535e-117">これによって、秘密キーにアクセスできない人物によってストアド プロシージャのコードが変更されることを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="7535e-117">This prevents someone who does not have access to the private key from changing the stored procedure code.</span></span> <span data-ttu-id="7535e-118">そのため、プロシージャを変更するたびに署名し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7535e-118">Therefore you must re-sign the procedure each time you modify it.</span></span>  
  
 <span data-ttu-id="7535e-119">モジュールへの署名は、次の 4 つの手順で行います。</span><span class="sxs-lookup"><span data-stu-id="7535e-119">There are four steps involved in signing a module:</span></span>  
  
1.  <span data-ttu-id="7535e-120">Transact-SQL ステートメント `CREATE CERTIFICATE [certificateName]` を使用して、証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="7535e-120">Create a certificate using the Transact-SQL `CREATE CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="7535e-121">このステートメントには、開始日、終了日、パスワードを設定するためのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="7535e-121">This statement has several options for setting a start and end date and a password.</span></span> <span data-ttu-id="7535e-122">既定の有効期限は 1 年間です。</span><span class="sxs-lookup"><span data-stu-id="7535e-122">The default expiration date is one year</span></span>  
  
2.  <span data-ttu-id="7535e-123">Transact-SQL ステートメント `CREATE USER [userName] FROM CERTIFICATE [certificateName]` を使用して、証明書に関連付けられたデータベース ユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7535e-123">Create a database user associated with that certificate using the Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="7535e-124">このユーザーはデータベース内のみに存在し、ログインには関連付けられません。</span><span class="sxs-lookup"><span data-stu-id="7535e-124">This user exists in the database only and is not associated with a login.</span></span>  
  
3.  <span data-ttu-id="7535e-125">証明書ユーザーに、データベース オブジェクトに対して必要な権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="7535e-125">Grant the certificate user the required permissions on the database objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7535e-126">証明書では、DENY ステートメントを使用して権限が取り消されているユーザーに権限を与えることはできません。</span><span class="sxs-lookup"><span data-stu-id="7535e-126">A certificate cannot grant permissions to a user that has had permissions revoked using the DENY statement.</span></span> <span data-ttu-id="7535e-127">DENY は常に GRANT よりも優先されるため、証明書ユーザーに許可された権限を呼び出し元が継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="7535e-127">DENY always takes precedence over GRANT, preventing the caller from inheriting permissions granted to the certificate user.</span></span>  
  
1.  <span data-ttu-id="7535e-128">Transact-SQL ステートメント `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` を使用して、証明書によってプロシージャに署名します。</span><span class="sxs-lookup"><span data-stu-id="7535e-128">Sign the procedure with the certificate using the Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` statement.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="7535e-129">外部リソース</span><span class="sxs-lookup"><span data-stu-id="7535e-129">External Resources</span></span>  
 <span data-ttu-id="7535e-130">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7535e-130">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="7535e-131">リソース</span><span class="sxs-lookup"><span data-stu-id="7535e-131">Resource</span></span>|<span data-ttu-id="7535e-132">説明</span><span class="sxs-lookup"><span data-stu-id="7535e-132">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7535e-133">[モジュール署名](http://go.microsoft.com/fwlink/?LinkId=98590)SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="7535e-133">[Module Signing](http://go.microsoft.com/fwlink/?LinkId=98590) in SQL Server Books Online</span></span>|<span data-ttu-id="7535e-134">モジュールの署名について説明し、サンプル シナリオと、関連する Transact-SQL のトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="7535e-134">Describes module signing, providing a sample scenario and links to the relevant Transact-SQL topics.</span></span>|  
|<span data-ttu-id="7535e-135">[証明書でストアド プロシージャの署名](http://msdn.microsoft.com/library/bb283630.aspx)SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="7535e-135">[Signing Stored Procedures with a Certificate](http://msdn.microsoft.com/library/bb283630.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="7535e-136">証明書を使用したストアド プロシージャの署名のチュートリアルです。</span><span class="sxs-lookup"><span data-stu-id="7535e-136">Provides a tutorial for signing a stored procedure with a certificate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7535e-137">参照</span><span class="sxs-lookup"><span data-stu-id="7535e-137">See Also</span></span>  
 [<span data-ttu-id="7535e-138">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="7535e-138">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="7535e-139">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="7535e-139">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="7535e-140">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="7535e-140">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="7535e-141">SQL Server でのストアド プロシージャを使用したアクセス許可の管理</span><span class="sxs-lookup"><span data-stu-id="7535e-141">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="7535e-142">SQL Server での安全な動的 SQL の作成</span><span class="sxs-lookup"><span data-stu-id="7535e-142">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="7535e-143">SQL Server での借用を使用したアクセス許可のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="7535e-143">Customizing Permissions with Impersonation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [<span data-ttu-id="7535e-144">ストアド プロシージャでのデータの変更</span><span class="sxs-lookup"><span data-stu-id="7535e-144">Modifying Data with Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="7535e-145">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="7535e-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
