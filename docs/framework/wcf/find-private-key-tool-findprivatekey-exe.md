---
title: "秘密キー検索ツール (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f542e0ba3bf35319c270fe9f93d3f355cc45ac95
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="d4e81-102">秘密キー検索ツール (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="d4e81-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>
<span data-ttu-id="d4e81-103">このコマンド ライン ツールを使用して、証明書ストアから秘密キーを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d4e81-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="d4e81-104">たとえば、FindPrivateKey.exe を使用して、証明書ストア内の特定の X.509 証明書に関連付けられている秘密キー ファイルの場所と名前を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="d4e81-104">For example, FindPrivateKey.exe can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4e81-105">FindPrivateKey ツールは、WCF のサンプルとして付属しています。</span><span class="sxs-lookup"><span data-stu-id="d4e81-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="d4e81-106">このサンプルの検索場所とビルド方法の詳細については、</span><span class="sxs-lookup"><span data-stu-id="d4e81-106">For more information about where to find the sample and how to build it, see</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e81-107">構文</span><span class="sxs-lookup"><span data-stu-id="d4e81-107">Syntax</span></span>  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a><span data-ttu-id="d4e81-108">コメント</span><span class="sxs-lookup"><span data-stu-id="d4e81-108">Remarks</span></span>  
 <span data-ttu-id="d4e81-109">次の表では、秘密キー検索ツール (FindPrivateKey.exe) で使用できる引数とオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d4e81-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>  
  
|<span data-ttu-id="d4e81-110">引数</span><span class="sxs-lookup"><span data-stu-id="d4e81-110">Argument</span></span>|<span data-ttu-id="d4e81-111">説明</span><span class="sxs-lookup"><span data-stu-id="d4e81-111">Description</span></span>|  
|--------------|-----------------|  
|`storeName`|<span data-ttu-id="d4e81-112">証明書ストアの名前。</span><span class="sxs-lookup"><span data-stu-id="d4e81-112">Name of the certificate store.</span></span>|  
|`storeLocation`|<span data-ttu-id="d4e81-113">証明書ストアの場所。</span><span class="sxs-lookup"><span data-stu-id="d4e81-113">The location of the certificate store.</span></span>|  
  
|<span data-ttu-id="d4e81-114">オプション</span><span class="sxs-lookup"><span data-stu-id="d4e81-114">Option</span></span>|<span data-ttu-id="d4e81-115">説明</span><span class="sxs-lookup"><span data-stu-id="d4e81-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d4e81-116">`/n <`*subjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="d4e81-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="d4e81-117">証明書のサブジェクト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4e81-117">Specifies the subject name of the certificate.</span></span>|  
|<span data-ttu-id="d4e81-118">`/t <`*拇印*`>`</span><span class="sxs-lookup"><span data-stu-id="d4e81-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="d4e81-119">証明書のサムプリントを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4e81-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="d4e81-120">Certmgr.exe を使用して証明書のサムプリントを取得します。</span><span class="sxs-lookup"><span data-stu-id="d4e81-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|  
|`/f`|<span data-ttu-id="d4e81-121">ファイル名だけを出力します。</span><span class="sxs-lookup"><span data-stu-id="d4e81-121">Outputs the file name only.</span></span>|  
|`/d`|<span data-ttu-id="d4e81-122">ディレクトリだけを出力します。</span><span class="sxs-lookup"><span data-stu-id="d4e81-122">Outputs the directory only.</span></span>|  
|`/a`|<span data-ttu-id="d4e81-123">絶対ファイル名を出力します。</span><span class="sxs-lookup"><span data-stu-id="d4e81-123">Outputs the absolute file name.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="d4e81-124">例</span><span class="sxs-lookup"><span data-stu-id="d4e81-124">Examples</span></span>  
 <span data-ttu-id="d4e81-125">次のコマンドは、John Doe の秘密キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="d4e81-125">The following command retrieves the private key for John Doe.</span></span>  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 <span data-ttu-id="d4e81-126">次のコマンドは、ローカル マシンの秘密キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="d4e81-126">The following command retrieves the private key for the local machine.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
