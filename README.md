# CustomToastfy

```
component custom toast =>

import React from 'react';

import { IconToastError, IconToastSucess, IconToastWarn } from '~/assets/icons';

import { Container,  IconContainer } from './styles';

interface CustomToastData {
  title?: string;
  message: string;
  status: 'success' | 'warn' | 'error';
}

export const CustomToast = ({ title, message, status }: CustomToastData) => {
  function Icon() {
    return (
      <>
        {status === 'success' && <IconToastSucess />}
        {status === 'warn' && <IconToastWarn />}
        {status === 'error' && <IconToastError />}
      </>
    );
  }

  return (
    <>
      <Container>
        <IconContainer>
          <Icon />
        </IconContainer>
        <div className="message">
          {!!title && <span>{title}</span>}
          <p>{message}</p>
        </div>
      </Container>
    </>
  );
};
```

```
css custom toast => 

import styled from 'styled-components';

export const Container = styled.div`
  display: flex;
  align-items: center;
  position: relative;
  width: 100%;
  position: absolute;
  inset: 13px 0;
  z-index: 9999999999999999999;

  span {
    color: var(--text-high);
    font-weight: 600;
    font-size: 1.3rem;
  }

  p {
    color: var(--text);
    padding-right: 0.5rem;
    font-weight: 400;
    font-size: 1.3rem;
  }

  .message {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
`;

export const IconContainer = styled.div`
  margin: 0 1rem;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
`;
```


```
app => 

 import { ToastContainer } from 'react-toastify';
import 'react-toastify/dist/ReactToastify.css';
 // No app

jsx (
<ToastContainer toastClassName="toastifyContainer" hideProgressBar />
)_


global css => .Toastify__toast-container {
    z-index: 99999999 !important;
  }
  
 
 exemple call component => 

 // NA FUNCTION QUE FOR CHAMAR O TOST

toast(
        <CustomToast
          status="success"
          title="Parabéns!"
          message="Cadastro realizado com sucesso."
        />,
        {
          icon: false,
          autoClose: 5000,
        }
      );
```
