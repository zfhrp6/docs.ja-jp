---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="d9d9a-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="d9d9a-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="d9d9a-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="d9d9a-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d9a-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9d9a-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d9d9a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d9d9a-105">Methods</span></span>  
 <span data-ttu-id="d9d9a-106">WSAT_TraceRecord クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="d9d9a-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d9d9a-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d9d9a-107">Properties</span></span>  
 <span data-ttu-id="d9d9a-108">WSAT_TraceRecord クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="d9d9a-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="d9d9a-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="d9d9a-109">ActivityID</span></span>  
 <span data-ttu-id="d9d9a-110">データ型: object</span><span class="sxs-lookup"><span data-stu-id="d9d9a-110">Data type: object</span></span>  
<span data-ttu-id="d9d9a-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d9d9a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d9a-112">トレース レコードのアクティビティ ID です。</span><span class="sxs-lookup"><span data-stu-id="d9d9a-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="d9d9a-113">EventID</span><span class="sxs-lookup"><span data-stu-id="d9d9a-113">EventID</span></span>  
 <span data-ttu-id="d9d9a-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="d9d9a-114">Data type: sint32</span></span>  
<span data-ttu-id="d9d9a-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d9d9a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d9a-116">トレース レコードのイベント ID です。</span><span class="sxs-lookup"><span data-stu-id="d9d9a-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="d9d9a-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="d9d9a-117">TraceRecord</span></span>  
 <span data-ttu-id="d9d9a-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="d9d9a-118">Data type: string</span></span>  
<span data-ttu-id="d9d9a-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d9d9a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d9a-120">トレース レコード</span><span class="sxs-lookup"><span data-stu-id="d9d9a-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d9a-121">要件</span><span class="sxs-lookup"><span data-stu-id="d9d9a-121">Requirements</span></span>  
  
|<span data-ttu-id="d9d9a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="d9d9a-122">MOF</span></span>|<span data-ttu-id="d9d9a-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="d9d9a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d9d9a-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="d9d9a-124">Namespace</span></span>|<span data-ttu-id="d9d9a-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="d9d9a-125">Defined in root\ServiceModel</span></span>|
