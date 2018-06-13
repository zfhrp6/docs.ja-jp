---
title: Cert2spc.exe (ソフトウェア発行元証明書テスト ツール)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c1d1944ae06ea26ce9bf7b4726e79155768d444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405302"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="b023b-102">Cert2spc.exe (ソフトウェア発行元証明書テスト ツール)</span><span class="sxs-lookup"><span data-stu-id="b023b-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="b023b-103">ソフトウェア発行元証明書テスト ツールは、1 つ以上の X.509 証明書からソフトウェア発行元証明書 (SPC: Software Publisher's Certificate) を作成します。</span><span class="sxs-lookup"><span data-stu-id="b023b-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="b023b-104">Cert2spc.exe はテスト専用のツールです。</span><span class="sxs-lookup"><span data-stu-id="b023b-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="b023b-105">有効な SPC は、VeriSign や Thawte などの証明書発行機関から入手できます。</span><span class="sxs-lookup"><span data-stu-id="b023b-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="b023b-106">X.509 証明書の作成の詳細については、「[Makecert.exe (証明書作成ツール)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b023b-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span></span>  
  
 <span data-ttu-id="b023b-107">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b023b-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="b023b-108">このツールを実行するには、開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b023b-108">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="b023b-109">詳細については、「[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b023b-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="b023b-110">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="b023b-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b023b-111">構文</span><span class="sxs-lookup"><span data-stu-id="b023b-111">Syntax</span></span>  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b023b-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b023b-112">Parameters</span></span>  
  
|<span data-ttu-id="b023b-113">引数</span><span class="sxs-lookup"><span data-stu-id="b023b-113">Argument</span></span>|<span data-ttu-id="b023b-114">説明</span><span class="sxs-lookup"><span data-stu-id="b023b-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="b023b-115">SPC ファイルに組み込む X.509 証明書の名前。</span><span class="sxs-lookup"><span data-stu-id="b023b-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="b023b-116">スペースで区切ることによって、複数の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b023b-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="b023b-117">SPC ファイルに組み込む証明書失効リストの名前。</span><span class="sxs-lookup"><span data-stu-id="b023b-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="b023b-118">スペースで区切ることによって、複数の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b023b-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="b023b-119">X.509 証明書が格納される PKCS #7 オブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="b023b-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="b023b-120">オプション</span><span class="sxs-lookup"><span data-stu-id="b023b-120">Option</span></span>|<span data-ttu-id="b023b-121">説明</span><span class="sxs-lookup"><span data-stu-id="b023b-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b023b-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="b023b-122">**/?**</span></span>|<span data-ttu-id="b023b-123">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="b023b-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="b023b-124">使用例</span><span class="sxs-lookup"><span data-stu-id="b023b-124">Examples</span></span>  
 <span data-ttu-id="b023b-125">`myCertificate.cer` から SPC を作成し、`mySPCFile.spc` に格納するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="b023b-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="b023b-126">`oneCertificate.cer` と `twoCertificate.cer` から SPC を作成し、`mySPCFile.spc` に格納するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="b023b-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="b023b-127">参照</span><span class="sxs-lookup"><span data-stu-id="b023b-127">See Also</span></span>  
 [<span data-ttu-id="b023b-128">ツール</span><span class="sxs-lookup"><span data-stu-id="b023b-128">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="b023b-129">Makecert.exe (証明書作成ツール)</span><span class="sxs-lookup"><span data-stu-id="b023b-129">Makecert.exe (Certificate Creation Tool)</span></span>](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [<span data-ttu-id="b023b-130">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="b023b-130">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
