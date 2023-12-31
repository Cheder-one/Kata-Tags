```
const FilmCard = styled(Row)(css`
  width: 28rem;
  height: 17.5rem;
  flex-shrink: 0;
`);

const Poster = styled.img`
  ${({ srcImg }) => css`
    content: url('${IMAGE_DOMAIN}/w220_and_h330_face${srcImg}');
  `}
`;

```
