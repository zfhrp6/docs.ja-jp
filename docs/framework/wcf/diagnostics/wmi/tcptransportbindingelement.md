---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9aa7e0d9eaba0181b17b44da1bf871c10af814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="52a08-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="52a08-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="52a08-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="52a08-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a08-104">構文</span><span class="sxs-lookup"><span data-stu-id="52a08-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="52a08-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="52a08-105">Methods</span></span>  
 <span data-ttu-id="52a08-106">TcpTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="52a08-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="52a08-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52a08-107">Properties</span></span>  
 <span data-ttu-id="52a08-108">TcpTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="52a08-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="52a08-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="52a08-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="52a08-110">データ型 : TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="52a08-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="52a08-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="52a08-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52a08-112">接続プールの設定。</span><span class="sxs-lookup"><span data-stu-id="52a08-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="52a08-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="52a08-113">ListenBacklog</span></span>  
 <span data-ttu-id="52a08-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="52a08-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="52a08-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="52a08-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52a08-116">保留可能なキュー内の接続要求の最大数です。</span><span class="sxs-lookup"><span data-stu-id="52a08-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="52a08-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="52a08-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="52a08-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="52a08-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="52a08-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="52a08-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52a08-120">TCP ポート共有をこの接続で有効にするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="52a08-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="52a08-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="52a08-121">TeredoEnabled</span></span>  
 <span data-ttu-id="52a08-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="52a08-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="52a08-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="52a08-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52a08-124">Teredo (ファイアウォールの内側にあるクライアントをアドレス指定するためのテクノロジ) を有効にするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="52a08-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52a08-125">要件</span><span class="sxs-lookup"><span data-stu-id="52a08-125">Requirements</span></span>  
  
|<span data-ttu-id="52a08-126">MOF</span><span class="sxs-lookup"><span data-stu-id="52a08-126">MOF</span></span>|<span data-ttu-id="52a08-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="52a08-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="52a08-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="52a08-128">Namespace</span></span>|<span data-ttu-id="52a08-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="52a08-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52a08-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="52a08-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
