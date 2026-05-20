# Reliability Checklist - FIT4110 Lab 03 (A4 AI Vision)

## 1. Functional tests

- [x] Co test cho endpoint health.
- [x] Co test happy path cho endpoint chinh.
- [x] Co kiem tra status code 2xx.
- [x] Co kiem tra field quan trong trong response.
- [x] Co it nhat 1 test doc du lieu chi tiet (GET by id, model info).

## 2. Auth tests

- [x] Co test thieu token.
- [x] Co test sai token.
- [x] Endpoint public duoc khai bao ro (health).
- [x] Test the hien expected status 401/403 tren local; mock co ghi chu hanh vi Prism.

## 3. Negative tests

- [x] Co test thieu field bat buoc.
- [x] Co test sai kieu du lieu / format (mediaUrl invalid).
- [x] Co test boundary id invalid.
- [x] Loi tra ve theo model error (ProblemDetails/ErrorResponse).

## 4. Boundary tests

- [x] Co test gia tri bien cho id/khong ton tai.
- [x] Co test truy van ket qua job/frame theo id.
- [x] Co ghi chu ky vong xu ly du lieu bien trong test-case matrix.
- [x] Co scenario unknown resource (404 hoac payload trang thai).

## 5. Reliability tests co ban

- [x] Co kiem tra response time (folder 06_Local_only_NonFunctional).
- [x] Co mo ta timeout/SLA < 1000ms cho local.
- [ ] Chua co test retry/idempotency rieng (se bo sung neu service local co logic).
- [x] Co consumer-side smoke test voi A2 va A6 vao A4.

## 6. Evidence

- [x] Collection export JSON: postman/collections/FIT4110_lab03_ai_vision.postman_collection.json
- [x] Environment mock export JSON: postman/environments/FIT4110_lab03_mock.postman_environment.json
- [x] Environment local export JSON: postman/environments/FIT4110_lab03_local.postman_environment.json
- [x] Newman report XML/HTML trong reports/ (mock)
- [x] Test-case matrix da dien.
- [x] Bien ban handshake da dien.
