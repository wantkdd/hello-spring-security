# 과제2 구현 요구사항 점검표

## GitHub / 실행 증빙
- Fork/clone 기반 Repository: `https://github.com/wantkdd/hello-spring-security`
- 기능 구현 커밋: `feat`, `fix` 접두사를 사용한 7회 이상 커밋
- 실행 화면: 공통 footer에 실습 수행 일시, 학번, 성명을 표시

## Spring Data JPA 페이징 & 검색
- `ProductRepository`에서 `@Query`와 `Pageable`을 함께 사용
- `ProductService`에서 `Page<Product>` 반환
- `ProductController`에서 `page`, `size`, `keyword` 파라미터를 받아 `PageRequest` 생성
- Thymeleaf 목록 화면에서 `productPage.content`, 이전/다음/페이지 번호, 검색어 유지 처리
- 샘플 상품 20개 기준 `size=5`일 때 총 4페이지 구성

## 상품 수정 기능
- `GET /products/{id}/edit`: ADMIN 전용 수정 폼 표시
- `POST /products/{id}/edit`: 검증 후 상품 수정 저장
- 서비스 계층 `@Transactional` 안에서 영속 엔티티 필드를 변경해 Dirty Checking으로 반영
- `ROLE_USER` 접근 시 403 안내 화면 표시

## 비밀번호 변경 기능
- `/user/password`는 인증 사용자만 접근 가능
- 현재 비밀번호는 `BCryptPasswordEncoder.matches()`로 검증
- 새 비밀번호는 `passwordEncoder.encode()` 결과만 저장
- 현재 비밀번호 불일치 시 저장하지 않고 오류 메시지 표시

## 보고서 구성
- 표지 → Security 필터 체인 아키텍처 → JPA 페이징 코드 분석 → Dirty Checking/BCrypt 코드 분석 → 기능별 실행 화면 → 학습 소감/자기평가체크리스트 순서로 작성
