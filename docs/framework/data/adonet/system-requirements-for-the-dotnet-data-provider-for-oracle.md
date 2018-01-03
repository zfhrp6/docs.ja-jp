---
title: ".NET Framework Data Provider for Oracle のシステム要件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cb21a71a548766ee5439c6a558ea7f23d1f45364
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a><span data-ttu-id="8241c-102">.NET Framework Data Provider for Oracle のシステム要件</span><span class="sxs-lookup"><span data-stu-id="8241c-102">System Requirements for the .NET Framework Data Provider for Oracle</span></span>
<span data-ttu-id="8241c-103">.NET Framework Data Provider for Oracle を使用するには、MDAC (Microsoft Data Access Components) のバージョン 2.6 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="8241c-103">The .NET Framework Data Provider for Oracle requires Microsoft Data Access Components (MDAC) version 2.6 or later.</span></span> <span data-ttu-id="8241c-104">MDAC 2.8 SP1 をインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8241c-104">MDAC 2.8 SP1 is recommended.</span></span>  
  
 <span data-ttu-id="8241c-105">Oracle 8i Release 3 (8.1.7) Client 以降もインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8241c-105">You must also have Oracle 8i Release 3 (8.1.7) Client or later installed.</span></span>  
  
 <span data-ttu-id="8241c-106">UTF16 は Oracle 9i の新機能なので、Oracle 9i 以前のバージョンの Oracle Client ソフトウェアでは UTF16 データベースにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="8241c-106">Oracle Client software prior to version Oracle 9i cannot access UTF16 databases because UTF16 is a new feature in Oracle 9i.</span></span> <span data-ttu-id="8241c-107">この機能を使用するには、お使いのクライアント ソフトウェアを Oracle 9i 以降にアップグレードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8241c-107">To use this feature, you must upgrade your client software to Oracle 9i or later.</span></span>  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a><span data-ttu-id="8241c-108">Data Provider for Oracle と Unicode データの使用</span><span class="sxs-lookup"><span data-stu-id="8241c-108">Working with the Data Provider for Oracle and Unicode Data</span></span>  
 <span data-ttu-id="8241c-109">.NET Framework Data Provider for Oracle および Oracle クライアント ライブラリを使用するときに考慮が必要な、Unicode に関連する問題の一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="8241c-109">Following is a list of Unicode-related issues that you should consider when working with the .NET Framework Data Provider for Oracle and Oracle client libraries.</span></span> <span data-ttu-id="8241c-110">詳細については、Oracle のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8241c-110">For more information, see your Oracle documentation.</span></span>  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a><span data-ttu-id="8241c-111">接続文字列の属性に Unicode 値を設定する</span><span class="sxs-lookup"><span data-stu-id="8241c-111">Setting the Unicode Value in a Connection String Attribute</span></span>  
 <span data-ttu-id="8241c-112">Oracle を操作する場合、接続文字列の属性を使用し、</span><span class="sxs-lookup"><span data-stu-id="8241c-112">When working with Oracle, you can use the connection string attribute</span></span>  
  
```  
Unicode=True   
```  
  
 <span data-ttu-id="8241c-113">UTF-16 モードで Oracle クライアント ライブラリを初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="8241c-113">to initialize the Oracle client libraries in UTF-16 mode.</span></span> <span data-ttu-id="8241c-114">これにより、Oracle クライアント ライブラリで、マルチバイト文字列の代わりに UTF-16 (UCS-2 とよく似ています) が使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8241c-114">This causes the Oracle client libraries to accept UTF-16 (which is very similar to UCS-2) instead of multi-byte strings.</span></span> <span data-ttu-id="8241c-115">新たに変換作業を行わなくても、Data Provider for Oracle で Oracle のコード ページを常に使用できます。</span><span class="sxs-lookup"><span data-stu-id="8241c-115">This allows the Data Provider for Oracle to always work with any Oracle code page without additional translation work.</span></span> <span data-ttu-id="8241c-116">この構成は、Oracle 9i クライアントを使用して、AL16UTF16 の代替文字セットを持つ Oracle 9i データベースと通信する場合に動作します。</span><span class="sxs-lookup"><span data-stu-id="8241c-116">This configuration only works if you are using Oracle 9i clients to communicate with an Oracle 9i database with the alternate character set of AL16UTF16.</span></span> <span data-ttu-id="8241c-117">その他のリソースが、Unicode に変換するために必要な Oracle 9i クライアントが Oracle 9i サーバーと通信を行うとき**CommandText**を適切なマルチ バイト文字の値を設定する 9i サーバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8241c-117">When an Oracle 9i client communicates with an Oracle 9i server, additional resources are required to convert the Unicode **CommandText** values to the appropriate multi-byte character set that the Oracle9i server uses.</span></span> <span data-ttu-id="8241c-118">安全な構成が確保されていることがわかっている場合は、`Unicode=True` を接続文字列に追加することにより回避することができます。</span><span class="sxs-lookup"><span data-stu-id="8241c-118">This can be avoided when you know that you have the safe configuration by adding `Unicode=True` to your connection string.</span></span>  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a><span data-ttu-id="8241c-119">Oracle クライアントと Oracle サーバーのバージョンの混在</span><span class="sxs-lookup"><span data-stu-id="8241c-119">Mixing Versions of Oracle Client and Oracle Server</span></span>  
 <span data-ttu-id="8241c-120">Oracle 8i クライアントがアクセスできない**NCHAR**、 **NVARCHAR2**、または**NCLOB**サーバーの各国語文字セットが AL16UTF16 として指定されている場合、Oracle 9i データベース内のデータ (既定の設定を Oracle 9i)。</span><span class="sxs-lookup"><span data-stu-id="8241c-120">Oracle 8i clients cannot access **NCHAR**, **NVARCHAR2**, or **NCLOB** data in Oracle 9i databases when the server's national character set is specified as AL16UTF16 (the default setting for Oracle 9i).</span></span> <span data-ttu-id="8241c-121">UTF-16 文字セットのサポートは Oracle 9i まで導入されなかったため、Oracle 8i クライアントでは読み取れません。</span><span class="sxs-lookup"><span data-stu-id="8241c-121">Because support for the UTF-16 character set was not introduced until Oracle 9i, Oracle 8i clients cannot read it.</span></span>  
  
### <a name="working-with-utf-8-data"></a><span data-ttu-id="8241c-122">UTF-8 データの使用</span><span class="sxs-lookup"><span data-stu-id="8241c-122">Working with UTF-8 Data</span></span>  
 <span data-ttu-id="8241c-123">代替文字セットを設定するには、レジストリ キー HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG を UTF8 に設定します。</span><span class="sxs-lookup"><span data-stu-id="8241c-123">To set the alternate character set, set the Registry Key HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG to UTF8.</span></span> <span data-ttu-id="8241c-124">詳細については、ご使用のプラットフォームに関する Oracle のインストール ノートを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8241c-124">See the Oracle Installation notes on your platform for more information.</span></span> <span data-ttu-id="8241c-125">既定の設定は、Oracle Client ソフトウェアのインストールに使用する言語の基本文字セットになっています。</span><span class="sxs-lookup"><span data-stu-id="8241c-125">The default setting is the primary character set of the language from which you are installing the Oracle Client software.</span></span> <span data-ttu-id="8241c-126">接続するデータベースの各国語文字セットと言語が一致するように設定されていないと、パラメーターと列の組み合わせは、各国語文字セットではなくプライマリ データベースの文字セットでデータを送受信します。</span><span class="sxs-lookup"><span data-stu-id="8241c-126">Not setting the language to match the national language character set of the database to which you are connecting will cause parameter and column bindings to send or receive data in your primary database character set, not the national character set.</span></span>  
  
### <a name="oraclelob-can-only-update-full-characters"></a><span data-ttu-id="8241c-127">OracleLob で更新できるのは Full 文字列のみです。</span><span class="sxs-lookup"><span data-stu-id="8241c-127">OracleLob Can Only Update Full Characters.</span></span>  
 <span data-ttu-id="8241c-128">ユーザビリティ上の理由から、<xref:System.Data.OracleClient.OracleLob>オブジェクトは、.NET Framework Stream クラスから継承し、提供**ReadByte**と**WriteByte**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8241c-128">For usability reasons, the <xref:System.Data.OracleClient.OracleLob> object inherits from the .NET Framework Stream class, and provides **ReadByte** and **WriteByte** methods.</span></span> <span data-ttu-id="8241c-129">メソッドも実装など**CopyTo**と**消去**その、Oracle のセクションで動作**LOB**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8241c-129">It also implements methods, such as **CopyTo** and **Erase**, that work on sections of Oracle **LOB** objects.</span></span> <span data-ttu-id="8241c-130">Oracle クライアント ソフトウェアが多数の文字を使用する Api を提供する一方、 **LOB**s (**CLOB**と**NCLOB**)。</span><span class="sxs-lookup"><span data-stu-id="8241c-130">In contrast, Oracle client software provides a number of APIs to work with character **LOB**s (**CLOB** and **NCLOB**).</span></span> <span data-ttu-id="8241c-131">ただし、これらの API は full 文字列でのみ動作します。</span><span class="sxs-lookup"><span data-stu-id="8241c-131">However, these APIs work on full characters only.</span></span> <span data-ttu-id="8241c-132">Data Provider for Oracle がサポートを実装するこの違いにより、**読み取り**と**ReadByte**バイトの方法で utf-16 データを操作します。</span><span class="sxs-lookup"><span data-stu-id="8241c-132">Because of this difference, the Data Provider for Oracle implements support for **Read** and **ReadByte** to work with UTF-16 data in a byte-wise manner.</span></span> <span data-ttu-id="8241c-133">ただし、他の方法、 **OracleLob**オブジェクトは full 文字列操作のみを許可します。</span><span class="sxs-lookup"><span data-stu-id="8241c-133">However, the other methods of the **OracleLob** object only allow full-character operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8241c-134">参照</span><span class="sxs-lookup"><span data-stu-id="8241c-134">See Also</span></span>  
 [<span data-ttu-id="8241c-135">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8241c-135">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="8241c-136">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="8241c-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
