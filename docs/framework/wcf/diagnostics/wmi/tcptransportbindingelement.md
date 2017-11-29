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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 180e954661319cb32edfd3180418fe9b1571ea5c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="e0783-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e0783-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="e0783-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e0783-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0783-104">構文</span><span class="sxs-lookup"><span data-stu-id="e0783-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e0783-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e0783-105">Methods</span></span>  
 <span data-ttu-id="e0783-106">TcpTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="e0783-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e0783-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e0783-107">Properties</span></span>  
 <span data-ttu-id="e0783-108">TcpTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="e0783-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="e0783-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e0783-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="e0783-110">データ型 : TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e0783-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="e0783-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e0783-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0783-112">接続プールの設定。</span><span class="sxs-lookup"><span data-stu-id="e0783-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="e0783-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="e0783-113">ListenBacklog</span></span>  
 <span data-ttu-id="e0783-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="e0783-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e0783-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e0783-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0783-116">保留可能なキュー内の接続要求の最大数です。</span><span class="sxs-lookup"><span data-stu-id="e0783-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="e0783-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="e0783-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="e0783-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="e0783-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e0783-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e0783-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0783-120">TCP ポート共有をこの接続で有効にするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="e0783-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="e0783-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="e0783-121">TeredoEnabled</span></span>  
 <span data-ttu-id="e0783-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="e0783-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="e0783-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e0783-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e0783-124">Teredo (ファイアウォールの内側にあるクライアントをアドレス指定するためのテクノロジ) を有効にするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="e0783-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0783-125">要件</span><span class="sxs-lookup"><span data-stu-id="e0783-125">Requirements</span></span>  
  
|<span data-ttu-id="e0783-126">MOF</span><span class="sxs-lookup"><span data-stu-id="e0783-126">MOF</span></span>|<span data-ttu-id="e0783-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="e0783-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e0783-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="e0783-128">Namespace</span></span>|<span data-ttu-id="e0783-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="e0783-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0783-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0783-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
