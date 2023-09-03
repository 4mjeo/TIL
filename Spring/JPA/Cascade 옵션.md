# Cascade 옵션

**Cascade 옵션?** 엔티티의 상태 변화를 전파시키는 옵션을 말함

- @OneToMany 나 @ManyToOne에 옵션으로 줄 수 있는 값
- 만약 엔티티의 상태 변화가 있으면 연관되어 있는 엔티티에도 상태 변화 전이시킴
- 기본적으로는 아무것도 전이시키지 않음

### Entity의 상태

---

1. Transient
2. Persistent
3. Detached
4. Removed

**cascade는 이러한 상태변화를 전이시키는 것!**
