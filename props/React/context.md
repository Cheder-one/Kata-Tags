```
import { PureComponent } from 'react';

class TimerProvider extends PureComponent {
	constructor(props) {
    super(props);

    this.state = {
      time: '',
    };
  }

	setTimerState = (newState, cb = () => null) => {
    this.setState(newState, () => cb(this.state));
  };

  render() {
    const { children } = this.props;

    const contextValue = {
      timerState: this.state,
      setTimerState: this.setTimerState,
    };

    return (
      <TimerContext.Provider value={contextValue}>
        {children}
      </TimerContext.Provider>
    );
  }
}

import { TimerContext } from '../../context';

class Timer extends Component {
	handleButtonClick = () => {
		const { timerState, setTimerState } = this.context;
		setTimerState({ timerValue: { min: '00', sec: '00' } });
	};

  render() {
    const { time } = this.state;
    const { min, sec } = time;

    return (
      <>
        <span className="todo-timer">{`${min}:${sec}`}</span>
        <button type="button" onClick={this.handleButtonClick} />
      </>
    );
  }
}

Timer.contextType = TimerContext; /=/ Важно

```

