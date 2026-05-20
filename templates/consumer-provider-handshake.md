# Consumer-Provider Handshake

## Thong tin chung

- Lab: FIT4110 Lab 03
- Ngay: 2026-05-20
- Provider team: A4 (AI Vision)
- Consumer team: A2 (Camera Stream), A6 (Core Business)
- Provider service: AI Vision
- Consumer service: Camera Stream / Core Business

## Contract

- Contract file: contracts/ai-vision.openapi.yaml
- Mock base URL: http://localhost:4011
- Auth method: Authorization Bearer token
- Endpoint duoc test:
  - POST /api/v1/vision/frame-detections
  - GET /api/v1/vision/frame-detections/{detectionId}
  - POST /api/v1/vision/analysis-jobs
  - GET /api/v1/vision/analysis-jobs/{jobId}

## Smoke test A2 -> A4

### Request

```http
POST /api/v1/vision/frame-detections
Authorization: Bearer <token>
Content-Type: application/json
```

```json
{
  "requestId": "smoke-a2-001",
  "cameraId": "CAM-A201-01",
  "roomId": "A201",
  "frameUrl": "https://storage.smart-campus.local/frames/cam-a201-01.jpg",
  "capturedAt": "2026-05-20T08:00:00Z",
  "analysisTypes": ["PERSON_DETECTION"]
}
```

### Expected response

```json
{
  "detectionId": "<uuid>",
  "requestId": "smoke-a2-001",
  "status": "PROCESSING"
}
```

## Smoke test A6 -> A4

### Request

```http
POST /api/v1/vision/analysis-jobs
Authorization: Bearer <token>
Content-Type: application/json
```

```json
{
  "requestId": "smoke-a6-001",
  "sourceService": "core-business",
  "sourceId": "incident-123",
  "mediaType": "IMAGE",
  "mediaUrl": "https://storage.smart-campus.local/incidents/frame-123.jpg",
  "roomId": "A203",
  "cameraId": "CAM-A203-02",
  "requestedAt": "2026-05-20T09:15:00Z",
  "analysisTypes": ["FIGHTING_DETECTION"]
}
```

### Expected response

```json
{
  "jobId": "<uuid>",
  "requestId": "smoke-a6-001",
  "status": "PROCESSING"
}
```

## Ket qua

- [x] Consumer goi mock thanh cong (A2, A6 -> A4).
- [x] Consumer parse duoc field can dung (detectionId/jobId, status).
- [x] Consumer hieu duoc loi 4xx/5xx theo ProblemDetails.
- [x] Co Newman report trong reports/.

## Ghi chu thay doi hop dong

| Noi dung | Truoc | Sau | Nguoi dong y |
|---|---|---|---|
| A4 contract | Mock toi thieu /detect | Full contract V2 /api/v1/vision/* | A4 |
| Smoke scope | 1 smoke generic | Tach 2 smoke A2 va A6 | A4 |

## Xac nhan

- Provider representative: A4 AI Vision owner
- Consumer representative: A2 Camera Stream owner, A6 Core Business owner
